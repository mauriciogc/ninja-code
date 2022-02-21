# Sumar números muy grandes

## Introducción

El tipo de valor `number` nos sirve para almacenar valores numéricos los cuales los usamos principalmente para contar, hacer cálculos y comparaciones.

Cuenta con tres valores simbólicos los cuales son:

- NaN (Not a number)
- Number.MAX_VALUE (aprox. 1.79E+308);
- Number.MIN_VALUE (aprox. 5e-324);

Esto quiere decir que JavaScript tiene una limitante de: “N” cantidad de dígitos

Si imprimimos en consola el número mayor y menor posible en JavaScript, nos arroja lo siguiente:

```javascript
console.log(Number.MAX_VALUE); //1.7976931348623157e+308
console.log(Number.MAX_VALUE); // 5e-324
```

Esto **NO** significa que sea el número con el que se puede trabajar en JavaScript ¿por que?... por el desbordamiento que tiene JavaScript.

`Number.MAX_SAFE_INTEGER` nos arroja el número máximo con el que podemos trabajar en JavaScript:

```javascript
console.log(Number.MAX_SAFE_INTEGER); // 9007199254740991
```

Veamos el siguiente ejemplo:

```javascript
console.log(Number.MAX_SAFE_INTEGER + 1); //9007199254740992
console.log(Number.MAX_SAFE_INTEGER + 2); //9007199254740992
console.log(Number.MAX_SAFE_INTEGER + 3); //9007199254740994
console.log(Number.MAX_SAFE_INTEGER + 4); //9007199254740996
console.log(Number.MAX_SAFE_INTEGER + 5); //9007199254740996
```

Podemos observar que la suma no es la esperada, y esta haciendo cosas "extrañas".

## Descripción

`BigInt` es un objeto contenedor que nos va a permitir representar y manipular valores primitivos, que son demasiado grandes para ser representados por el mismo tipo de dato primitivo.

## Sintaxis

La sintaxis básica es la siguiente:

```javascript
BigInt(number);
```

Ejemplo:

```javascript
console.log(BigInt(Number.MAX_SAFE_INTEGER)); //9007199254740991n
```

Podemos observar un “n” al final del número, este es un indicador que se está usando el objeto BigInt, si a un número le agregamos una “n” al final y validamos su tipo de dato, este nos regresará que es de tipo :

```javascript
console.log(BigInt(typeof 1n === 'bigint')); //true
console.log(BigInt(typeof BigInt('1') === 'bigint')); //true
```

Vamos a manipular el valor máximo seguro con el objeto `BigInt` y le sumaremos:

```javascript
console.log(BigInt(Number.MAX_SAFE_INTEGER) + BigInt(1)); //9007199254740992n
console.log(BigInt(Number.MAX_SAFE_INTEGER) + 2n); //9007199254740993n
console.log(BigInt(Number.MAX_SAFE_INTEGER) + BigInt(3)); //9007199254740994n
console.log(BigInt(Number.MAX_SAFE_INTEGER) + 4n); //9007199254740995n
console.log(BigInt(Number.MAX_SAFE_INTEGER) + BigInt(5)); //9007199254740996n
```

> **Recuerda:** Podemos manejar un número como si fuera un bigint agregando al final una `n`

Para manipular cantidades grandes, se sugiere trabajarlas con el tipo de dato `string`.

```javascript
console.log(BigInt('776593613551065310475986805093')); //776593613551065310475986805093n
```

Ya que si lo manipulamos como tipo `number`, corremos el riesgo de perder el número original.

```javascript
console.log(BigInt(776593613551065310475986805093)); //776593613551065369760633978880n
```

Podemos observar que los últimos dígitos ya no son los que eran originalmente.

Ejemplos:

```javascript
console.log(
  BigInt('776593613551065310475986805093') +
    BigInt('881490790365369734885614717497')
);
//1658084403916435045361601522590n
```

En vez de sumarlos, los vamos a multiplicar

```javascript
console.log(
  BigInt('776593613551065310475986805093') *
    BigInt('881490790365369734885614717497')
);
//684560118201827068570087146431244401754926904256736795812221n
```

Con formato:

```javascript
const bigNumber =
  BigInt('776593613551065310475986805093') *
  BigInt('881490790365369734885614717497');
console.log(bigNumber);
console.log(Intl.NumberFormat().format(bigNumber));
// 684,560,118,201,827,068,570,087,146,431,244,401,754,926,904,256,736,795,812,221
```
