---
title: mbrtoc16, mbrtoc323
ms.date: 11/04/2016
api_name:
- mbrtoc16
- mbrtoc32
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-convert-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbrtoc16
- mbrtoc32
- uchar/mbrtoc16
- uchar/mbrtoc32
helpviewer_keywords:
- mbrtoc16 function
- mbrtoc32 function
ms.assetid: 099ade4d-56f7-4e61-8b45-493f1d7a64bd
ms.openlocfilehash: 52bcec5911fdc2ecbb073ae0042777aa4eb2b963
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952442"
---
# <a name="mbrtoc16-mbrtoc32"></a>mbrtoc16, mbrtoc32

Convierte el primer carácter multibyte de una cadena estrecha en el carácter UTF-32 o UTF-16 equivalente.

## <a name="syntax"></a>Sintaxis

```C
size_t mbrtoc16(
   char16_t* destination,
   const char* source,
   size_t max_bytes,
   mbstate_t* state
);

size_t mbrtoc32(
   char32_t* destination,
   const char* source,
   size_t max_bytes,
   mbstate_t* state
);
```

### <a name="parameters"></a>Parámetros

*destino*<br/>
Puntero al equivalente de **char16_t** o **char32_t** del carácter multibyte que se va a convertir. Si es null, la función no almacena un valor.

*source*<br/>
Puntero a la cadena de caracteres multibyte que se va a convertir.

*max_bytes*<br/>
Número máximo de bytes en el *origen* para examinar un carácter que se va a convertir. Debe ser un valor entre uno y el número de bytes, incluidos los terminadores null, que permanecen en el *origen*.

*state*<br/>
Puntero a un objeto de estado de conversión **mbstate_t** usado para interpretar la cadena multibyte en uno o más caracteres de salida.

## <a name="return-value"></a>Valor devuelto

Si se ejecuta correctamente, devuelve el valor de la primera de estas condiciones que se aplica, dado el valor de *Estado* actual:

|Value|Condición|
|-----------|---------------|
|0|El siguiente *max_bytes* o menos caracteres convertidos desde el *origen* corresponden al carácter ancho nulo, que es el valor almacenado si *Destination* no es NULL.<br /><br /> el *Estado* contiene el estado de desplazamiento inicial.|
|Entre 1 y *max_bytes*, ambos incluidos|El valor devuelto es el número de bytes de *origen* que completan un carácter multibyte válido. El carácter ancho convertido se almacena si *Destination* no es NULL.|
|-3|El siguiente carácter ancho resultante de una llamada anterior a la función se ha almacenado en el *destino* si el *destino* no es NULL. Esta llamada a la función no consume bytes del *origen* .<br /><br /> Cuando el *origen* apunta a un carácter multibyte que requiere más de un carácter ancho para representar (por ejemplo, un par suplente), el valor de *Estado* se actualiza para que la siguiente llamada de función escriba el carácter adicional.|
|-2|Los siguientes *max_bytes* bytes representan un carácter multibyte incompleto pero potencialmente válido. No se almacena ningún valor en el *destino*. Este resultado puede producirse si *max_bytes* es cero.|
|-1|Se ha producido un error de codificación. El siguiente *max_bytes* o menos bytes no contribuyen a un carácter multibyte completo y válido. No se almacena ningún valor en el *destino*.<br /><br /> **EILSEQ** se almacena en **errno** y el estado de la conversión *no está especificado* .|

## <a name="remarks"></a>Comentarios

La función **mbrtoc16** lee hasta *max_bytes* bytes desde el *origen* para buscar el primer carácter multibyte válido y completo, y luego almacena el carácter UTF-16 equivalente en el *destino*. Los bytes de origen se interpretan según la configuración regional multibyte de subprocesos actual. Si el carácter multibyte requiere más de un carácter de salida UTF-16, como un par suplente, el valor de *Estado* se establece para almacenar el siguiente carácter UTF-16 en el *destino* en la siguiente llamada a **mbrtoc16**. La función **mbrtoc32** es idéntica, pero la salida se almacena como un carácter UTF-32.

Si el *origen* es null, estas funciones devuelven el equivalente de una llamada realizada con argumentos de **null** para el *destino*, **""** para el *origen*y 1 para *max_bytes*. Se omiten los valores pasados de *Destination* y *max_bytes* .

Si *source* no es null, la función comienza al principio de la cadena e inspecciona hasta *max_bytes* bytes para determinar el número de bytes necesarios para completar el siguiente carácter multibyte, incluidas las secuencias de desplazamiento. Si los bytes examinados contienen un carácter multibyte válido y completo, la función convierte el carácter en los caracteres anchos equivalentes de 16 o 32 bits. Si el *destino* no es null, la función almacena el primer carácter de resultado (y posiblemente único) en el destino. Si se requieren caracteres de salida adicionales, se establece un valor en el *Estado*, de modo que las llamadas subsiguientes a la función generen los caracteres adicionales y devuelvan el valor-3. Si no se requieren más caracteres de salida, el *Estado* se establece en el estado de desplazamiento inicial.

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**mbrtoc16**, **mbrtoc32**|\<uchar.h>|\<cuchar>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[c16rtomb, c32rtomb](c16rtomb-c32rtomb1.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbsrtowcs](mbsrtowcs.md)<br/>
[mbsrtowcs_s](mbsrtowcs-s.md)<br/>
