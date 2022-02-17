# Generar una Fecha 

### Descripción
En un principio `toLocaleDateString` dependia únicamente de la implementación y configuración de los navegadores, entonces, cuando se agregó la compatibilidad con el objeto `Intl` *(ECMAScript2015)*, se permitió que `toLocaleDateString` aceptara las mismas opciones.

El objeto `Intl` contiene métodos y constructores de la *API de internalización de ECMAScript*, es decir, tiene características no solo para *convertir fechas*, si no también *cadenas* y *números*.

### Sintaxis básica

```javascript
new Intl.DateTimeFormat().format();
```

La instancia del constructor `DateTimeFormat` tiene un *método* llamado `format` que es el encargado de devolver con formato una fecha dada, ejemplo: 

```javascript
let date = new Date('Wed Feb 10 2022 20:56:26 GMT-0600');
console.log(new Intl.DateTimeFormat().format(date)); //10/2/2022
```
> **Importante:** Si no le mandamos alguna fecha al método `format`, este nos va a devolver la fecha de hoy con el formato del navegador.

Para darle un formato más específico a la fecha, haremos uso de los dos posibles parámetros que usa el constructor `DateTimeFormat`:
- *locales*: Cadena o arreglo de cadenas que representan etiquetas de idioma (si no se agrega por default toma la del navegador)
- *options*: Propiedades que se utilizan para personalizar la salida

```javascript
new Intl.DateTimeFormat(locales, options).format(date);
```

#### Locales

```javascript
console.log(new Intl.DateTimeFormat('en-GB').format(date)); // 16/02/2022
console.log(new Intl.DateTimeFormat('cs-CZ').format(date)); // 16. 2. 2022
console.log(new Intl.DateTimeFormat('sv-SE').format(date)); // 2022-02-16
```

A continuación te dejo una lista con mas locales:

| Locales     | Formato       | Ejemplo        |
| ----------- | ------------- | -------------- |
| af-ZA       | d/M/yyyy      | 6/2/2022       |
| am-ET       | d/M/yyyy      | 6/2/2022       |
| ar-AE       | yyyy/M/dd     | ٦‏/٢‏/٢٠٢٢     |
| ar-BH       | yyyy/M/dd     | ٦‏/٢‏/٢٠٢٢     |
| ar-DZ       | d‏/M‏/yyyy    | 6‏/2‏/2022     |
| ar-EG       | yyyy/M/dd     | ٦‏/٢‏/٢٠٢٢     |
| ar-IQ       | yyyy/M/dd     | ٦‏/٢‏/٢٠٢٢     |
| ar-JO       | yyyy/M/dd     | ٦‏/٢‏/٢٠٢٢     |
| ar-KW       | yyyy/M/dd     | ٦‏/٢‏/٢٠٢٢     |
| ar-LB       | yyyy/M/dd     | ٦‏/٢‏/٢٠٢٢     |
| ar-LY       | d‏/M‏/yyyy    | 6‏/2‏/2022     |
| ar-MA       | d‏/M‏/yyyy    | 6‏/2‏/2022     |
| ar-OM       | yyyy/M/dd     | ٦‏/٢‏/٢٠٢٢     |
| ar-QA       | yyyy/M/dd     | ٦‏/٢‏/٢٠٢٢     |
| ar-SA       | yyyy/M/dd     | ٥‏/٧‏/١٤٤٣ هـ  |
| ar-SY       | yyyy/M/dd     | ٦‏/٢‏/٢٠٢٢     |
| ar-TN       | d‏/M‏/yyyy    | 6‏/2‏/2022     |
| ar-YE       | yyyy/M/dd     | ٦‏/٢‏/٢٠٢٢     |
| arn-CL      | d/M/yyyy      | 6/2/2022       |
| as-IN       | d/M/yyyy      | 6/2/2022       |
| az-Cyrl-AZ  | dd.MM.yyyy    | 06.02.2022     |
| az-Latn-AZ  | yyyy-M-d      | 2022-2-6       |
| ba-RU       | d/M/yyyy      | 6/2/2022       |
| be-BY       | d/M/yyyy      | 6/2/2022       |
| bg-BG       | dd.MM.yyyy r. | 06.02.2022 r.  |
| bn-BD       | d/M/yyyy      | ৬/২/২০২২       |
| bn-IN       | d/M/yyyy      | ৬/২/২০২২       |
| bo-CN       | d/M/yyyy      | 6/2/2022       |
| br-FR       | d/M/yyyy      | 6/2/2022       |
| bs-Cyrl-BA  | dd.MM.yyyy.   | 06.02.2022.    |
| bs-Latn-BA  | yyyy-M-d      | 2022-2-6       |
| ca-ES       | d/M/yyyy      | 6/2/2022       |
| co-FR       | d/M/yyyy      | 6/2/2022       |
| cs-CZ       | d. M. yyyy    | 6\. 2. 2022    |
| cy-GB       | d/M/yyyy      | 6/2/2022       |
| da-DK       | d.M.yyyy      | 6.2.2022       |
| de-AT       | d.M.yyyy      | 6.2.2022       |
| de-CH       | d.M.yyyy      | 6.2.2022       |
| de-DE       | d.M.yyyy      | 6.2.2022       |
| de-LI       | d.M.yyyy      | 6.2.2022       |
| de-LU       | d.M.yyyy      | 6.2.2022       |
| dsb-DE      | d/M/yyyy      | 6/2/2022       |
| dv-MV       | d/M/yyyy      | 6/2/2022       |
| el-GR       | d/M/yyyy      | 6/2/2022       |
| en-029      | M/d/yyyy      | 2/6/2022       |
| en-AU       | dd/MM/yyyy    | 06/02/2022     |
| en-BZ       | dd/MM/yyyy    | 06/02/2022     |
| en-CA       | yyyy-MM-dd    | 2022-02-06     |
| en-GB       | dd/MM/yyyy    | 06/02/2022     |
| en-IE       | d/M/yyyy      | 6/2/2022       |
| en-IN       | d/M/yyyy      | 6/2/2022       |
| en-JM       | dd/MM/yyyy    | 06/02/2022     |
| en-MY       | dd/MM/yyyy    | 06/02/2022     |
| en-NZ       | dd/MM/yyyy    | 06/02/2022     |
| en-PH       | dd/MM/yyyy    | 06/02/2022     |
| en-SG       | dd/MM/yyyy    | 06/02/2022     |
| en-TT       | dd/MM/yyyy    | 06/02/2022     |
| en-US       | M/d/yyyy      | 2/6/2022       |
| en-ZA       | yyyy/MM/dd    | 2022/02/06     |
| en-ZW       | d/M/yyyy      | 6/2/2022       |
| es-AR       | d/M/yyyy      | 6/2/2022       |
| es-BO       | d/M/yyyy      | 6/2/2022       |
| es-CL       | dd-MM-yyyy    | 06-02-2022     |
| es-CO       | d/M/yyyy      | 6/2/2022       |
| es-CR       | d/M/yyyy      | 6/2/2022       |
| es-DO       | d/M/yyyy      | 6/2/2022       |
| es-EC       | d/M/yyyy      | 6/2/2022       |
| es-ES       | d/M/yyyy      | 6/2/2022       |
| es-GT       | d/M/yyyy      | 6/2/2022       |
| es-HN       | d/M/yyyy      | 6/2/2022       |
| es-MX       | d/M/yyyy      | 6/2/2022       |
| es-NI       | d/M/yyyy      | 6/2/2022       |
| es-PA       | MM/dd/yyyy    | 02/06/2022     |
| es-PE       | d/M/yyyy      | 6/2/2022       |
| es-PR       | MM/dd/yyyy    | 02/06/2022     |
| es-PY       | d/M/yyyy      | 6/2/2022       |
| es-SV       | d/M/yyyy      | 6/2/2022       |
| es-US       | d/M/yyyy      | 6/2/2022       |
| es-UY       | d/M/yyyy      | 6/2/2022       |
| es-VE       | d/M/yyyy      | 6/2/2022       |
| et-EE       | d.M.yyyy      | 6.2.2022       |
| eu-ES       | d/M/yyyy      | 6/2/2022       |
| fa-IR       | yyyy/MM/dd    | ۱۴۰۰/۱۱/۱۷     |
| fi-FI       | d.M.yyyy      | 6.2.2022       |
| fil-PH      | M/d/yyyy      | 2/6/2022       |
| fo-FO       | d/M/yyyy      | 6/2/2022       |
| fr-BE       | dd/MM/yyyy    | 06/02/2022     |
| fr-CA       | yyyy-MM-dd    | 2022-02-06     |
| fr-CH       | dd.MM.yyyy    | 06.02.2022     |
| fr-FR       | dd/MM/yyyy    | 06/02/2022     |
| fr-LU       | dd/MM/yyyy    | 06/02/2022     |
| fr-MC       | dd/MM/yyyy    | 06/02/2022     |
| fy-NL       | d/M/yyyy      | 6/2/2022       |
| ga-IE       | d/M/yyyy      | 6/2/2022       |
| gd-GB       | d/M/yyyy      | 6/2/2022       |
| gl-ES       | d/M/yyyy      | 6/2/2022       |
| gsw-FR      | d/M/yyyy      | 6/2/2022       |
| gu-IN       | d/M/yyyy      | 6/2/2022       |
| ha-Latn-NG  | d/M/yyyy      | 6/2/2022       |
| he-IL       | d.M.yyyy      | 6.2.2022       |
| hi-IN       | d/M/yyyy      | 6/2/2022       |
| hr-BA       | dd. MM. yyyy. | 06\. 02. 2022. |
| hr-HR       | dd. MM. yyyy. | 06\. 02. 2022. |
| hsb-DE      | d/M/yyyy      | 6/2/2022       |
| hu-HU       | yyyy. MM. dd. | 2022\. 02. 06. |
| hy-AM       | d/M/yyyy      | 6/2/2022       |
| id-ID       | d/M/yyyy      | 6/2/2022       |
| ig-NG       | d/M/yyyy      | 6/2/2022       |
| ii-CN       | d/M/yyyy      | 6/2/2022       |
| is-IS       | d/M/yyyy      | 6/2/2022       |
| it-CH       | d/M/yyyy      | 6/2/2022       |
| it-IT       | d/M/yyyy      | 6/2/2022       |
| iu-Cans-CA  | d/M/yyyy      | 6/2/2022       |
| iu-Latn-CA  | d/M/yyyy      | 6/2/2022       |
| ja-JP       | yyyy/M/d      | 2022/2/6       |
| ka-GE       | d/M/yyyy      | 6/2/2022       |
| kk-KZ       | d/M/yyyy      | 6/2/2022       |
| kl-GL       | d/M/yyyy      | 6/2/2022       |
| km-KH       | d/M/yyyy      | 6/2/2022       |
| kn-IN       | d/M/yyyy      | 6/2/2022       |
| ko-KR       | yyyy. M. d.   | 2022\. 2. 6.   |
| kok-IN      | d/M/yyyy      | 6/2/2022       |
| ky-KG       | d/M/yyyy      | 6/2/2022       |
| lb-LU       | d/M/yyyy      | 6/2/2022       |
| lo-LA       | d/M/yyyy      | 6/2/2022       |
| lt-LT       | yyyy-MM-dd    | 2022-02-06     |
| lv-LV       | yyyy.MM.dd.   | 2022.02.06.    |
| mi-NZ       | d/M/yyyy      | 6/2/2022       |
| mk-MK       | d/M/yyyy      | 6/2/2022       |
| ml-IN       | d/M/yyyy      | 6/2/2022       |
| mn-MN       | d/M/yyyy      | 6/2/2022       |
| mn-Mong-CN  | d/M/yyyy      | 6/2/2022       |
| moh-CA      | d/M/yyyy      | 6/2/2022       |
| mr-IN       | d/M/yyyy      | ६/२/२०२२       |
| ms-BN       | d/M/yyyy      | 6/2/2022       |
| ms-MY       | d/M/yyyy      | 6/2/2022       |
| mt-MT       | d/M/yyyy      | 6/2/2022       |
| nb-NO       | d.M.yyyy      | 6.2.2022       |
| ne-NP       | d/M/yyyy      | 6/2/2022       |
| nl-BE       | d/M/yyyy      | 6/2/2022       |
| nl-NL       | d-M-yyyy      | 6-2-2022       |
| nn-NO       | d/M/yyyy      | 6/2/2022       |
| nso-ZA      | d/M/yyyy      | 6/2/2022       |
| oc-FR       | d/M/yyyy      | 6/2/2022       |
| or-IN       | d/M/yyyy      | 6/2/2022       |
| pa-IN       | yyyy-M-d      | 2022-2-6       |
| pl-PL       | dd.MM.yyyy    | 06.02.2022     |
| prs-AF      | yyyy/MM/dd    | ۱۴۰۰/۱۱/۱۷     |
| ps-AF       | d/M/yyyy      | 6/2/2022       |
| pt-BR       | dd/MM/yyyy    | 06/02/2022     |
| pt-PT       | dd/MM/yyyy    | 06/02/2022     |
| qut-GT      | d/M/yyyy      | 6/2/2022       |
| quz-BO      | d/M/yyyy      | 6/2/2022       |
| quz-EC      | d/M/yyyy      | 6/2/2022       |
| quz-PE      | d/M/yyyy      | 6/2/2022       |
| rm-CH       | d/M/yyyy      | 6/2/2022       |
| ro-RO       | dd.MM.yyyy    | 06.02.2022     |
| ru-RU       | dd.MM.yyyy    | 06.02.2022     |
| rw-RW       | d/M/yyyy      | 6/2/2022       |
| sa-IN       | d/M/yyyy      | 6/2/2022       |
| sah-RU      | d/M/yyyy      | 6/2/2022       |
| se-FI       | d/M/yyyy      | 6/2/2022       |
| se-NO       | d/M/yyyy      | 6/2/2022       |
| se-SE       | d/M/yyyy      | 6/2/2022       |
| si-LK       | d/M/yyyy      | 6/2/2022       |
| sk-SK       | d. M. yyyy    | 6\. 2. 2022    |
| sl-SI       | d. M. yyyy    | 6\. 2. 2022    |
| sma-NO      | d/M/yyyy      | 6/2/2022       |
| sma-SE      | d/M/yyyy      | 6/2/2022       |
| smj-NO      | d/M/yyyy      | 6/2/2022       |
| smj-SE      | d/M/yyyy      | 6/2/2022       |
| smn-FI      | d/M/yyyy      | 6/2/2022       |
| sms-FI      | d/M/yyyy      | 6/2/2022       |
| sq-AL       | d/M/yyyy      | 6/2/2022       |
| sr-Cyrl-BA  | d.M.yyyy.     | 6.2.2022.      |
| sr-Cyrl-CS  | d.M.yyyy.     | 6.2.2022.      |
| sr-Cyrl-ME  | d.M.yyyy.     | 6.2.2022.      |
| sr-Cyrl-RS  | d.M.yyyy.     | 6.2.2022.      |
| sr-Latn-BA  | d.M.yyyy.     | 6.2.2022.      |
| sr-Latn-CS  | d.M.yyyy.     | 6.2.2022.      |
| sr-Latn-ME  | d.M.yyyy.     | 6.2.2022.      |
| sr-Latn-RS  | d.M.yyyy.     | 6.2.2022.      |
| sv-FI       | yyyy-MM-dd    | 2022-02-06     |
| sv-SE       | yyyy-MM-dd    | 2022-02-06     |
| sw-KE       | d/M/yyyy      | 6/2/2022       |
| syr-SY      | d/M/yyyy      | 6/2/2022       |
| ta-IN       | d/M/yyyy      | 6/2/2022       |
| te-IN       | d/M/yyyy      | 6/2/2022       |
| tg-Cyrl-TJ  | d/M/yyyy      | 6/2/2022       |
| th-TH       | d/M/M5d5      | 6/2/2565       |
| tk-TM       | d/M/yyyy      | 6/2/2022       |
| tn-ZA       | d/M/yyyy      | 6/2/2022       |
| tr-TR       | dd.MM.yyyy    | 06.02.2022     |
| tt-RU       | d/M/yyyy      | 6/2/2022       |
| tzm-Latn-DZ | d/M/yyyy      | 6/2/2022       |
| ug-CN       | d/M/yyyy      | 6/2/2022       |
| uk-UA       | dd.MM.yyyy    | 06.02.2022     |
| ur-PK       | d/M/yyyy      | 6/2/2022       |
| uz-Cyrl-UZ  | dd/MM/yyyy    | 06/02/2022     |
| uz-Latn-UZ  | yyyy-M-d      | 2022-2-6       |
| vi-VN       | d/M/yyyy      | 6/2/2022       |
| wo-SN       | d/M/yyyy      | 6/2/2022       |
| xh-ZA       | d/M/yyyy      | 6/2/2022       |
| yo-NG       | d/M/yyyy      | 6/2/2022       |
| zh-CN       | yyyy/M/d      | 2022/2/6       |
| zh-HK       | d/M/yyyy      | 6/2/2022       |
| zh-MO       | d/M/yyyy      | 6/2/2022       |
| zh-SG       | yyyy年M月d日     | 2022年2月6日      |
| zh-TW       | yyyy/M/d      | 2022/2/6       |
| zu-ZA       | d/M/yyyy      | 6/2/2022       |


#### Options

Las opciones que acepta el constructor como segundo parámetro son:

```javascript
{
  weekday: 'narrow' | 'short' | 'long',
  era: 'narrow' | 'short' | 'long',
  year: 'numeric' | '2-digit',
  month: 'numeric' | '2-digit' | 'narrow' | 'short' | 'long',
  day: 'numeric' | '2-digit',
  hour: 'numeric' | '2-digit',
  minute: 'numeric' | '2-digit',
  second: 'numeric' | '2-digit',
  timeZoneName: 'short' | 'long',
  timeZone: 'Asia/Shanghai', // HUSO De horario expresado
  hour12: true | false, // Forzar formato 12hrs o 24hrs
  
  dateStyle: 'long | medium | short',
  timeStyle: 'long | medium | short',
}

```

Veamos algunos ejemplos: 

Tomaremos de referencia esta fecha:
```javascript
let date = new Date('Wed Feb 6 2022 20:56:26 GMT-0600');
```

Vamos a ocupar tipo `es-MX`, para que nos regrese el formato en español de México:
```javascript
console.log(new Intl.DateTimeFormat('es-MX').format(date)); //output 6/2/2022
```

Vamos a construir uno que tenga el día numérico a 1 dígito, que el mes sea la palabra completa y el año este a 4 dígitos:
```javascript
const options = { day: 'numeric', month: 'long', year: 'numeric' };
console.log(new Intl.DateTimeFormat('es-MX', options).format(date));
//output 6 de febrero de 2022
```

Vamos a construir uno que tenga el día numérico a 2 dígitos, que el mes este abreviado y nos muestre la hora en formato de 24hrs:
```javascript
const options = { day: "2-digit", month: "short",  timeStyle: "long" };
console.log(new Intl.DateTimeFormat('es-MX', options).format(date));
//output 06-feb. 20:56:26
```

Tenemos dos propiedades que va a simplificar un poco el resultado, veamos: 
```javascript
const options = {dateStyle: "long", timeStyle: "long" };
console.log(new Intl.DateTimeFormat('es-MX', options).format(date));
// 6 de febrero de 2022, 20:56:26 GMT-6
```


