# Generar una Fecha 

## Descripción
El objeto `Intl.NumberFormat` es un constructor de objetos que permiten el formato de números sensibles al idioma.


## Sintaxis

La sintaxis básica es la siguiente:
```javascript
new Intl.NumberFormat();
```

La instancia del constructor `NumberFormat` tiene los siguientes métodos: 
- `resolvedOptions`
- `format`
- `formatToParts`

### `NumberFormat.resolvedOptions()`

`resolvedOptions` es el encargado de devolver la configuración que tenemos en el navegador con relación al formato numérico que tiene el navegador

```javascript
console.log(new Intl.NumberFormat().resolvedOptions());
/* 
{
  locale: "es-MX"
  maximumFractionDigits: 3
  minimumFractionDigits: 0
  minimumIntegerDigits: 1
  notation: "standard"
  numberingSystem: "latn"
  signDisplay: "auto"
  style: "decimal"
  useGrouping: true
}
*/
```

### `NumberFormat.format()`

`format` es el encargado de devolver un número con un formato por default o especificado: 
```javascript
console.log(new Intl.NumberFormat().format(10000)); // 10,000
console.log(new Intl.NumberFormat().format("10000")); // 10,000
```
> **Importante:** Si utilizamos la forma básica, este nos devolverá el número con el formato que tiene por default el navegador. 
> **Recuerda**: No olvides que puede aceptar números con el tipo de dato `number` o `string`.

Para darle un formato más específico al número, haremos uso de los dos posibles parámetros que usa el constructor `DateTimeFormat`:
- *locales* 
- *options* 

```javascript
new Intl.NumberFormat(locales, options).format(number);
```

#### Locales
Cadena o arreglo de cadenas que representan etiquetas de idioma (si no se agrega por default toma la del navegador)

```javascript
const number = 10000000;
console.log(new Intl.NumberFormat('es-MX').format(number)); // 10,000,000
console.log(new Intl.NumberFormat('es-ES').format(number)); // 10.000.000
console.log(new Intl.NumberFormat('sv-SE').format(number)); // 10 000 000
```

A continuación te dejo una lista con mas locales:

| Tipo        | Ejemplo     |
| ----------- | ----------- |
| af-ZA       | 10,000,000  |
| am-ET       | 10,000,000  |
| ar-DZ       | 10.000.000  |
| ar-LY       | 10.000.000  |
| ar-MA       | 10.000.000  |
| ar-TN       | 10.000.000  |
| arn-CL      | 10,000,000  |
| as-IN       | 10,000,000  |
| az-Cyrl-AZ  | 10.000.000  |
| az-Latn-AZ  | 10,000,000  |
| ba-RU       | 10,000,000  |
| be-BY       | 10,000,000  |
| bg-BG       | 10 000 000  |
| bo-CN       | 10,000,000  |
| br-FR       | 10,000,000  |
| bs-Cyrl-BA  | 10.000.000  |
| bs-Latn-BA  | 10,000,000  |
| ca-ES       | 10.000.000  |
| co-FR       | 10,000,000  |
| cs-CZ       | 10 000 000  |
| cy-GB       | 10,000,000  |
| da-DK       | 10.000.000  |
| de-AT       | 10 000 000  |
| de-CH       | 10’000’000  |
| de-DE       | 10.000.000  |
| de-LI       | 10’000’000  |
| de-LU       | 10.000.000  |
| dsb-DE      | 10,000,000  |
| dv-MV       | 10,000,000  |
| el-GR       | 10.000.000  |
| en-029      | 10,000,000  |
| en-AU       | 10,000,000  |
| en-BZ       | 10,000,000  |
| en-CA       | 10,000,000  |
| en-GB       | 10,000,000  |
| en-IE       | 10,000,000  |
| en-IN       | 1,00,00,000 |
| en-JM       | 10,000,000  |
| en-MY       | 10,000,000  |
| en-NZ       | 10,000,000  |
| en-PH       | 10,000,000  |
| en-SG       | 10,000,000  |
| en-TT       | 10,000,000  |
| en-US       | 10,000,000  |
| en-ZA       | 10 000 000  |
| en-ZW       | 10,000,000  |
| es-AR       | 10.000.000  |
| es-BO       | 10.000.000  |
| es-CL       | 10.000.000  |
| es-CO       | 10.000.000  |
| es-CR       | 10 000 000  |
| es-DO       | 10,000,000  |
| es-EC       | 10.000.000  |
| es-ES       | 10.000.000  |
| es-GT       | 10,000,000  |
| es-HN       | 10,000,000  |
| es-MX       | 10,000,000  |
| es-NI       | 10,000,000  |
| es-PA       | 10,000,000  |
| es-PE       | 10,000,000  |
| es-PR       | 10,000,000  |
| es-PY       | 10.000.000  |
| es-SV       | 10,000,000  |
| es-US       | 10,000,000  |
| es-UY       | 10.000.000  |
| es-VE       | 10.000.000  |
| et-EE       | 10 000 000  |
| eu-ES       | 10,000,000  |
| fa-IR       | ۱۰٬۰۰۰٬۰۰۰  |
| fi-FI       | 10 000 000  |
| fil-PH      | 10,000,000  |
| fo-FO       | 10,000,000  |
| fr-BE       | 10 000 000  |
| fr-CA       | 10 000 000  |
| fr-CH       | 10 000 000  |
| fr-FR       | 10 000 000  |
| fr-LU       | 10.000.000  |
| fr-MC       | 10 000 000  |
| fy-NL       | 10,000,000  |
| ga-IE       | 10,000,000  |
| gd-GB       | 10,000,000  |
| gl-ES       | 10,000,000  |
| gsw-FR      | 10,000,000  |
| gu-IN       | 1,00,00,000 |
| ha-Latn-NG  | 10,000,000  |
| he-IL       | 10,000,000  |
| hi-IN       | 1,00,00,000 |
| hr-BA       | 10.000.000  |
| hr-HR       | 10.000.000  |
| hsb-DE      | 10,000,000  |
| hu-HU       | 10 000 000  |
| hy-AM       | 10,000,000  |
| id-ID       | 10.000.000  |
| ig-NG       | 10,000,000  |
| ii-CN       | 10,000,000  |
| is-IS       | 10,000,000  |
| it-CH       | 10’000’000  |
| it-IT       | 10.000.000  |
| iu-Cans-CA  | 10,000,000  |
| iu-Latn-CA  | 10,000,000  |
| ja-JP       | 10,000,000  |
| ka-GE       | 10,000,000  |
| kk-KZ       | 10,000,000  |
| kl-GL       | 10,000,000  |
| km-KH       | 10,000,000  |
| kn-IN       | 10,000,000  |
| ko-KR       | 10,000,000  |
| kok-IN      | 10,000,000  |
| ky-KG       | 10,000,000  |
| lb-LU       | 10,000,000  |
| lo-LA       | 10,000,000  |
| lt-LT       | 10 000 000  |
| lv-LV       | 10 000 000  |
| mi-NZ       | 10,000,000  |
| mk-MK       | 10,000,000  |
| ml-IN       | 1,00,00,000 |
| mn-MN       | 10,000,000  |
| mn-Mong-CN  | 10,000,000  |
| moh-CA      | 10,000,000  |
| mr-IN       | १,००,००,००० |
| ms-BN       | 10.000.000  |
| ms-MY       | 10,000,000  |
| mt-MT       | 10,000,000  |
| nb-NO       | 10 000 000  |
| ne-NP       | 10,000,000  |
| nl-BE       | 10.000.000  |
| nl-NL       | 10.000.000  |
| nn-NO       | 10,000,000  |
| nso-ZA      | 10,000,000  |
| oc-FR       | 10,000,000  |
| or-IN       | 10,000,000  |
| pa-IN       | 10,000,000  |
| pl-PL       | 10 000 000  |
| prs-AF      | ۱۰٬۰۰۰٬۰۰۰  |
| ps-AF       | 10,000,000  |
| pt-BR       | 10.000.000  |
| pt-PT       | 10 000 000  |
| qut-GT      | 10,000,000  |
| quz-BO      | 10,000,000  |
| quz-EC      | 10,000,000  |
| quz-PE      | 10,000,000  |
| rm-CH       | 10,000,000  |
| ro-RO       | 10.000.000  |
| ru-RU       | 10 000 000  |
| rw-RW       | 10,000,000  |
| sa-IN       | 10,000,000  |
| sah-RU      | 10,000,000  |
| se-FI       | 10,000,000  |
| se-NO       | 10,000,000  |
| se-SE       | 10,000,000  |
| si-LK       | 10,000,000  |
| sk-SK       | 10 000 000  |
| sl-SI       | 10.000.000  |
| sma-NO      | 10,000,000  |
| sma-SE      | 10,000,000  |
| smj-NO      | 10,000,000  |
| smj-SE      | 10,000,000  |
| smn-FI      | 10,000,000  |
| sms-FI      | 10,000,000  |
| sq-AL       | 10,000,000  |
| sr-Cyrl-BA  | 10.000.000  |
| sr-Cyrl-CS  | 10.000.000  |
| sr-Cyrl-ME  | 10.000.000  |
| sr-Cyrl-RS  | 10.000.000  |
| sr-Latn-BA  | 10.000.000  |
| sr-Latn-CS  | 10.000.000  |
| sr-Latn-ME  | 10.000.000  |
| sr-Latn-RS  | 10.000.000  |
| sv-FI       | 10 000 000  |
| sv-SE       | 10 000 000  |
| sw-KE       | 10,000,000  |
| syr-SY      | 10,000,000  |
| ta-IN       | 1,00,00,000 |
| te-IN       | 1,00,00,000 |
| tg-Cyrl-TJ  | 10,000,000  |
| th-TH       | 10,000,000  |
| tk-TM       | 10,000,000  |
| tn-ZA       | 10,000,000  |
| tr-TR       | 10.000.000  |
| tt-RU       | 10,000,000  |
| tzm-Latn-DZ | 10,000,000  |
| ug-CN       | 10,000,000  |
| uk-UA       | 10 000 000  |
| ur-PK       | 10,000,000  |
| uz-Cyrl-UZ  | 10 000 000  |
| uz-Latn-UZ  | 10,000,000  |
| vi-VN       | 10.000.000  |
| wo-SN       | 10,000,000  |
| xh-ZA       | 10,000,000  |
| yo-NG       | 10,000,000  |
| zh-CN       | 10,000,000  |
| zh-HK       | 10,000,000  |
| zh-MO       | 10,000,000  |
| zh-TW       | 10,000,000  |
| zu-ZA       | 10,000,000  |



#### Options
Propiedades que se utilizan para personalizar la salida. Las opciones que acepta el constructor como segundo parámetro son:
```javascript
{
    notation: 'standard | scientific | engineering | compact',
    compactDisplay: 'short | long', // Utilizar si notation:compact,
    
    style: 'currency | decimal | percent | unit',
    currency: 'USD | EUR | CNY | MXN ...', //Utilizar si style:currency,
    currencyDisplay: 'symbol | code | name',
    useGrouping: true | false,
    minimumIntegerDigits: '1-21 digitos',
    minimumFractionDigits: '0-21 digitos',
    maximumFractionDigits: '0-21 digitos',
    minimumSignificantDigits: '1-21 digitos',
    maximumSignificantDigits: '1-21 digitos',
    
    unit: 'kilometer | meter | centimeter | liter ...',
    unitDisplay: 'long | short'
}
```

Vamos a construir la cantidad en moneda mexicana.
```javascript
const number = 1234567890.1234;
const options = {
    style: "currency",
    currency: "MXN"
};
console.log(new Intl.NumberFormat('es-MX', options).format(number)); //$1,234,567,890.12
```

Vamos a construir la cantidad en moneda europea, pero con dos tipos de locale (Mexicano y Español).
```javascript
const number = 1234567890.1234;
const options = {
    style: 'currency',
    currency: 'EUR'
};
console.log(new Intl.NumberFormat('es-MX', options).format(number)); // EUR 1,234,567,890.12
console.log(new Intl.NumberFormat('es-ES', options).format(number)); // 1.234.567.890,12 €
```

Vamos a construir una cantidad que nos diga el formato de la moneda, pero no como símbolo.
```javascript
const number = 1234567890.1234;
const options = {
    style: 'currency',
    currency: 'MXN',
    currencyDisplay: 'name',
};
console.log(new Intl.NumberFormat('es-MX', options).format(number)); // 1,234,567,890.12 pesos mexicanos
console.log(new Intl.NumberFormat('es-ES', options).format(number)); // 1.234.567.890,12 pesos mexicanos
```

> **Nota:** Para ver todos los formatos currency [link](https://www.six-group.com/en/products-services/financial-information/data-standards.html#scrollTo=maintenance-agency)

Vamos a construir una cantidad que nos devuelva al menos 4 digitos decimales.
```javascript
const number = 1234567890.1234;
const options = {
    minimumFractionDigits: 4
};

console.log(new Intl.NumberFormat('es-MX', options).format(number)); //1,234,567,890.1234
```

Vamos a construir una cantidad con las unidades de kilometros.
```javascript
const number = 1234567890.1234;
const options = {
    style: 'unit',
    unit: 'kilometer',
    unitDisplay: 'long'
};

console.log(new Intl.NumberFormat('es-MX', options).format(number)); // 1,234,567,890.123 kilómetros
```

> Para ver todas las unidades [link](https://tc39.es/proposal-unified-intl-numberformat/section6/locales-currencies-tz_proposed_out.html#sec-issanctionedsimpleunitidentifier)


### `NumberFormat.formatToParts()`

`formatToParts` es el encargado de devolver una cantidad en un arreglo de objetos, veamos un ejemplo:
```javascript
const number = 1234567890.1234;
console.log(new Intl.NumberFormat().formatToParts(number));
/*
[
  0: {type: 'integer', value: '1'}
  1: {type: 'group', value: ','}
  2: {type: 'integer', value: '234'}
  3: {type: 'group', value: ','}
  4: {type: 'integer', value: '567'}
  5: {type: 'group', value: ','}
  6: {type: 'integer', value: '890'}
  7: {type: 'decimal', value: '.'}
  8: {type: 'fraction', value: '123'}
]
*/
```


