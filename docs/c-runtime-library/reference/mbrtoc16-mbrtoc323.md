---
title: mbrtoc16, mbrtoc323
ms.date: 4/2/2020
api_name:
- mbrtoc16
- mbrtoc32
- _o_mbrtoc16
- _o_mbrtoc32
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 0e3d5ceffa5adc9e9f6ba96cccb46a3fbcfca69a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919563"
---
# <a name="mbrtoc16-mbrtoc32"></a>mbrtoc16, mbrtoc32

Convierte el primer carácter multibyte UTF-8 de una cadena en el carácter UTF-16 o UTF-32 equivalente.

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

*destino*\
Puntero a la **char16_t** o **char32_t** equivalente del carácter multibyte UTF-8 que se va a convertir. Si es null, la función no almacena un valor.

*fuentes*\
Puntero a la cadena de caracteres multibyte UTF-8 que se va a convertir.

*max_bytes*\
Número máximo de bytes en el *origen* para examinar un carácter que se va a convertir. Este argumento debe ser un valor entre uno y el número de bytes, incluidos los terminadores null, que permanecen en el *origen*.

*State*\
Puntero a un objeto de estado de conversión de **mbstate_t** utilizado para interpretar la cadena multibyte UTF-8 en uno o varios caracteres de salida.

## <a name="return-value"></a>Valor devuelto

Si se ejecuta correctamente, devuelve el valor de la primera de estas condiciones que se aplica, dado el valor de *Estado* actual:

|Value|Condición|
|-----------|---------------|
|0|El siguiente *max_bytes* o menos caracteres convertidos desde el *origen* corresponden al carácter ancho nulo, que es el valor almacenado si el *destino* no es NULL.<br /><br /> el *Estado* contiene el estado de desplazamiento inicial.|
|Entre 1 y *max_bytes*, ambos incluidos|El valor devuelto es el número de bytes de *origen* que completan un carácter multibyte válido. El carácter ancho convertido se almacena si el *destino* no es NULL.|
|-3|El siguiente carácter ancho resultante de una llamada anterior a la función se ha almacenado en el *destino* si el *destino* no es NULL. Esta llamada a la función no consume bytes del *origen* .<br /><br /> Cuando el *origen* apunta a un carácter multibyte UTF-8 que requiere más de un carácter ancho para representar (por ejemplo, un par suplente), el valor de *Estado* se actualiza para que la siguiente llamada de función escriba el carácter adicional.|
|-2|Los siguientes *max_bytes* bytes representan un carácter multibyte UTF-8 incompleto, pero potencialmente válido. No se almacena ningún valor en el *destino*. Este resultado puede producirse si *max_bytes* es cero.|
|-1|Se ha producido un error de codificación. La siguiente *max_bytes* o menos bytes no contribuyen a un carácter multibyte UTF-8 completo y válido. No se almacena ningún valor en el *destino*.<br /><br /> **EILSEQ** se almacena en **errno** y el *Estado* del valor de estado de la conversión no está especificado.|

## <a name="remarks"></a>Observaciones

La función **mbrtoc16** lee hasta *max_bytes* bytes desde el *origen* para encontrar el primer carácter multibyte UTF-8 válido y completo y, a continuación, almacena el carácter UTF-16 equivalente en el *destino*. Si el carácter requiere más de un carácter de salida UTF-16, como un par suplente, el valor de *Estado* se establece para almacenar el siguiente carácter UTF-16 en el *destino* en la siguiente llamada a **mbrtoc16**. La función **mbrtoc32** es idéntica, pero la salida se almacena como un carácter UTF-32.

Si el *origen* es null, estas funciones devuelven el equivalente de una llamada realizada con argumentos de **null** para el *destino* `""` (una cadena vacía terminada en null) para el *origen*y 1 para *max_bytes*. Se omiten los valores pasados de *Destination* y *max_bytes* .

Si el *origen* no es null, la función comienza al principio de la cadena e inspecciona hasta *max_bytes* bytes para determinar el número de bytes necesarios para completar el siguiente carácter multibyte UTF-8, incluidas las secuencias de desplazamiento. Si los bytes examinados contienen un carácter multibyte UTF-8 válido y completo, la función convierte el carácter en caracteres anchos equivalentes de 16 ó 32 bits. Si el *destino* no es null, la función almacena el primer carácter de resultado (y posiblemente único) en el destino. Si se requieren caracteres de salida adicionales, se establece un valor en el *Estado*, de modo que las llamadas subsiguientes a la función generen los caracteres adicionales y devuelvan el valor-3. Si no se requieren más caracteres de salida, el *Estado* se establece en el estado de desplazamiento inicial.

Para convertir caracteres multibyte no UTF-8 en caracteres UTF-16 LE, use las funciones [varios bytes mbrtowc](mbrtowc.md), [mbtowc o _mbtowc_l](mbtowc-mbtowc-l.md) .

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**mbrtoc16**, **mbrtoc32**|\<uchar.h>|\<cuchar>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../compatibility.md).

## <a name="see-also"></a>Consulta también

[Conversión de datos](../data-conversion.md)\
[Configuración regional](../locale.md)\
[Interpretación de secuencias de caracteres multibyte](../interpretation-of-multibyte-character-sequences.md)\
[c16rtomb, c32rtomb](c16rtomb-c32rtomb1.md)\
[varios bytes mbrtowc](mbrtowc.md)\
[mbsrtowcs](mbsrtowcs.md)\
[mbsrtowcs_s](mbsrtowcs-s.md)
