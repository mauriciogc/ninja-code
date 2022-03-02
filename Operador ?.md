# El operador ?

## Introducción

El operador `?` se puede utilizar de 3 maneras diferentes:

- Como operador condicional (`condicional ? true : false`)
- Como encadenamiento opcional (`?.`, `?.()`, `?.[]`)
- Como operador coalescente nulo (`this value ?? other value`)

## Como Operador condicional

El operador condicional o ternario es el único operador en JavaScript que toma 3 operandos:

- Una condición seguida de un signo de interrogación `?`
- Una expresión para ejecutar si la condición es verdadera `true`, seguida de `:`
- Expresión para ejecutar si la condición es falsa `false`

La finalidad de este operador es tenerla como una alternativa a la declaración `if/else`.

La sintaxis básica es la siguiente:

```javascript
condition ? exprIfTrue : exprIfFalse;
```

Ejemplo:

```javascript
let age = 18;
let beverage = '';

if (age >= 18) {
  beverage = 'beer';
} else {
  beverage = 'juice';
}

console.log(beverage); //output beverage
```

Si aprovechamos al operador ? como ternario, quedaría de la siguiente manera:

```javascript
let age = 18;
let beverage = age >= 18 ? 'beer' : 'juice';
```

## Como Encadenamiento opcional

El operador de encadenamiento opcional `?.`, nos permite acceder al valor de una propiedad dentro de un objeto, con la ventaja de que nosotros **NO** debemos verificar si la referencia o encadenamiento de propiedades es válido.

Tenemos el siguiente ejemplo:

```javascript
const user = {
  name: 'Mauricio',
  address: {
    city: 'CDMX',
    geolocation: {
      coord: '19.4403392, -99.1840237',
    },
  },
};
console.log(user.address.geolocation.coord); //output '19.4403392, -99.1840237'
```

En el ejemplo anterior se ha accedido al valor por medio del encadenamiento de propiedades `prop1.prop2.propN`.

Otro ejemplo:

```javascript
const user = {
  name: 'Mauricio',
  address: {
    city: 'CDMX',
  },
};
console.log(user.address.geolocation.coord); //Error
```

En el ejemplo anterior podemos observar que el encadenamiento de propiedades no ha funcionado (arroja un error y truena nuestro código) ya que `geolocation.coord` no existen, la forma más rápida de solucionarlo es validando cada uno de las propiedades, es decir:

```javascript
const hasCoord =
  user &&
  user.address &&
  user.address.geolocation &&
  user.address.geolocation.coord;
if (hasCoord) {
  console.log(user.address.geolocation);
}
```

Ante esta problemática, podemos utilizar el "Operador de encadenamiento opcional", es decir es igual que el del encadenamiento normal, pero evitando que nuestro código arroje un error si la referencia es `null` o `undefined`, en vez de eso solo regresará `undefined`.

La sintaxis es la siguiente:

```javascript
obj.val?.prop;
```

Ejemplo:

```javascript
const user = {
  name: 'Mauricio',
};

console.log(user.address?.geolocation.coord); //output undefined
```

Lo que hace es validar si existe `address`, en caso de que **no exista** nos retorne `undefined`,.

Se debe tener cuidado, como el siguiente ejemplo:

```javascript
const user = {
  name: 'Mauricio',
  address: {
    city: 'CDMX',
  },
};
console.log(user.address?.geolocation.coord); //Error
```

Si prestamos atención, solo estamos indicando que `address` puede o no existir la propiedad, pero **NO** le indicamos que `geolocation` **sea opcional**, por lo que **nos retorna el error**, para solucionarlo, solo basta con indicarle que es opcional:

```javascript
console.log(user.address?.geolocation?.coord); //undefined
```

Utilizar el encadenamiento opcional, nos permite tener expresiones más cortas y simples:

```javascript
if (user.address?.geolocation?.coord) {
  console.log(user.address.geolocation.coord);
}
```

Además de validar las propiedades también permite hacerlo con arreglos y funciones, veamos la sinatxis:

```javascript
obj.val?.[expr]; //Como arreglo
obj.func?.(args); //Como función
```

Con funciones dentro de un objeto:

```javascript
let user = {
  name: 'Mauricio',
  address: {
    city: 'CDMX',
  },
  isAdmin() {
    return 'Yes';
  },
};

let user2 = {};

console.log(user.isAdmin?.()); //Yes
console.log(user2.isAdmin?.()); //undefined
```

Con arreglos dentro de un objeto:

```javascript
let user = {
  name: 'Mauricio',
  address: {
    city: 'CDMX',
  },
  isAdmin() {
    return 'Yes';
  },
  hobbies: ['foo', 'bar'],
};

let user2 = {};

console.log(user.hobbies?.[1]); //bar
console.log(user2.hobbies?.[1]); //undefined
```

> **IMPORTANTE**: El encadenamiento opcional no se puede usar en un objeto raíz no declarado, pero se puede usar con un objeto raíz no definido.
>
> **IMPORTANTE 2**: El encadenamiento opcional solo es de modo consulta, es decir que NO podemos funciona para escribir propiedades.

## Como operador coalescente nulo (Nullish coalescing operator)

El operador “nullish coalescing” viene a solucionar los problemas que se tienen con el operador OR `||`.

Ejemplos con el operador `||`:

```javascript
let number = 0;
const print = number || 80;
console.log(print); //output 80
```

En palabras mortales del ejemplo de arriba es: JavaScript ha intentado convertir el `0` en un valor `booleano`, y sabemos que `0 => false, 1 => true`, entonces al regresar ser `false`, nos retorna `80`

Lo mismo ocurre con los de tipo `string`:

```javascript
let str = '';
const print = str || 'Hello';
console.log(print); //output Hello
```

JavaScript ha intentado convertir `''` (vacío) en un valor `booleano`, y sabemos que `vacío => false, diferente de vacío => true`

Para solucionar este problema, se utiliza el operador “nullish coalescing”, se escribe con doble `??`.

La sintaxis es la siguiente:

```javascript
leftExpr ?? rightExpr;
```

Si la **expresión de la izquierda esta definida** será **ese valor**, caso **contrario** el **valor de la derecha**.

Ejemplos:

```javascript
let str = '';
const print = str ?? 'Hello';
console.log(print); //output ''

let number = 0;
const print = number ?? 100;
console.log(print); //output 0

let foo = null;
let bar == undefined:

console.log(foo ?? 'Hello'); //output Hello
console.log(bar ?? 'World'); //output World
```
