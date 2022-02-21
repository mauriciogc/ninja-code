# Recorrer un objeto

## Descripción

`Object` es la clase que representa un tipo de dato de JavaScript, es usado para guardar una colección de datos definidos y entidades complejas.

## Sintaxis

Para tratar un objeto como un arreglo, la clase `Object` tiene 3 métodos:

- `Object.keys`
- `Object.values`
- `Object.entries`

### `Object.keys()`

El método `Object.keys` devuelve un arreglo de las propiedades `clave` de un objeto.

```javascript
const person = {
  name: 'Mauricio',
  firstName: 'García',
  lastName: 'Camacho',
  gender: 'male',
  dob: '12 Junio',
  phone: '011-962-7516',
};

console.log(Object.keys(person));
// (6) ['name', 'firstName', 'lastName', 'gender', 'dob', 'phone']
```

Al devolver un `array` de tipo `string`, este puede ser tratado con como cualquier arreglo, es decir, lo podemos iterar con `map`, `filter`, `reduce`, `forEach`, `find`, `every`, `includes`, ...

### `Object.values()`

El método `Object.values()` devuelve un arreglo con los valores correspondientes a las propiedades enumerables de un objeto.

```javascript
const person = {
  name: 'Mauricio',
  firstName: 'García',
  lastName: 'Camacho',
  gender: 'male',
  dob: '12 Junio',
  phone: '011-962-7516',
};

console.log(Object.values(person));
// (6) ['Mauricio', 'García', 'Camacho', 'male', '12 Junio', '011-962-7516']
```

De la misma forma que el método `keys`, al devolver un `array` de tipo `string`, este puede ser tratado con como cualquier arreglo.

### `Object.entries()`

El método `Object.entries()` devuelve una matriz de pares propios de una propiedad enumerable [`key`, `value`] de un objeto dado.

```javascript
const person = {
  name: 'Mauricio',
  firstName: 'García',
  lastName: 'Camacho',
  gender: 'male',
  dob: '12 Junio',
  phone: '011-962-7516',
};

const arrPerson = Object.entries(person);

console.log(arrPerson);
/* 
0: (2) ['name', 'Mauricio']
1: (2) ['firstName', 'García']
2: (2) ['lastName', 'Camacho']
3: (2) ['gender', 'male']
4: (2) ['dob', '12 Junio']
5: (2) ['phone', '011-962-7516']
*/

arrPerson.forEach(([key, value]) => console.log(key, value));
/*
name Mauricio
firstName García
lastName Camacho
gender male
dob 12 Junio
phone 011-962-7516
*/
```

## Ventajas

Algunas ventajas de usar la clase `Object` y sus métodos `keys`, `values` o `entries`:

- Obtenemos de manera sencilla solo las claves.
- Obtenemos de manera sencilla solo los valores.
- No debemos de preocuparnos por las propiedades enumeradas de prototype.
- Puede ser tratado como un arreglo.
