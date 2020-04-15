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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 91755d19eacf73f19700eed7fffbffc529d4e235
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340978"
---
# <a name="mbrtoc16-mbrtoc32"></a>mbrtoc16, mbrtoc32

Traduce el primer carácter multibyte UTF-8 de una cadena en el carácter UTF-16 o UTF-32 equivalente.

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

*Destino*\
Puntero al **char16_t** o **char32_t** equivalente del carácter multibyte UTF-8 que se convertirá. Si null, la función no almacena un valor.

*Fuente*\
Puntero a la cadena de caracteres multibyte UTF-8 que se va a convertir.

*max_bytes*\
El número máximo de bytes en el *origen* que se va a examinar para que se convierta un carácter. Este argumento debe ser un valor entre uno y el número de bytes, incluido cualquier terminador nulo, que permanece en *el origen*.

*Estado*\
Puntero a un objeto de estado de conversión **de mbstate_t** utilizado para interpretar la cadena multibyte UTF-8 en uno o varios caracteres de salida.

## <a name="return-value"></a>Valor devuelto

En caso de éxito, devuelve el valor de la primera de estas condiciones que se aplica, dado el valor *de estado* actual:

|Value|Condición|
|-----------|---------------|
|0|La siguiente *max_bytes* o menos caracteres convertidos desde el *origen* corresponden al carácter ancho nulo, que es el valor almacenado si *destination* no es null.<br /><br /> *estado* contiene el estado de desplazamiento inicial.|
|Entre 1 y *max_bytes,* inclusive|El valor devuelto es el número de bytes de *origen* que completan un carácter multibyte válido. El carácter ancho convertido se almacena si *destination* no es null.|
|-3|El siguiente carácter ancho resultante de una llamada anterior a la función se ha almacenado en *destino* si *destination* no es null. Esta llamada a la función no consume bytes del *origen.*<br /><br /> Cuando *el origen* apunta a un carácter multibyte UTF-8 que requiere más de un carácter ancho para representar (por ejemplo, un par suplente), el valor de *estado* se actualiza para que la siguiente llamada de función escriba el carácter adicional.|
|-2|Los siguientes *bytes de max_bytes* representan un carácter multibyte UTF-8 incompleto, pero potencialmente válido. No se almacena ningún valor en *destino.* Este resultado puede producirse si *max_bytes* es cero.|
|-1|Se ha producido un error de codificación. Los siguientes *bytes max_bytes* o menos no contribuyen a un carácter multibyte UTF-8 completo y válido. No se almacena ningún valor en *destino.*<br /><br /> **EILSEQ** se almacena en **errno** y el *estado* del estado de conversión no se especifica.|

## <a name="remarks"></a>Observaciones

La función **mbrtoc16** lee hasta *max_bytes* bytes del *origen* para encontrar el primer carácter multibyte UTF-8 completo y válido y, a continuación, almacena el carácter UTF-16 equivalente en *destino.* Si el carácter requiere más de un carácter de salida UTF-16, como un par suplente, el valor de *estado* se establece para almacenar el siguiente carácter UTF-16 en *destino* en la siguiente llamada a **mbrtoc16**. La función **mbrtoc32** es idéntica, pero la salida se almacena como un carácter UTF-32.

Si *source* es null, estas funciones devuelven el equivalente de `""` una llamada realizada mediante argumentos de **NULL** para *destination*, (una cadena vacía terminada en null) para *source*y 1 para *max_bytes*. Se omiten los valores pasados de *destination* y *max_bytes.*

Si *source* no es null, la función comienza al principio de la cadena e inspecciona hasta *max_bytes* bytes para determinar el número de bytes necesarios para completar el siguiente carácter multibyte UTF-8, incluidas las secuencias de desplazamiento. Si los bytes examinados contienen un carácter multibyte UTF-8 válido y completo, la función convierte el carácter en caracteres o caracteres de 16 bits o 32 bits anchos equivalentes. Si *destination* no es null, la función almacena el primer (y posiblemente solo) carácter de resultado en el destino. Si se requieren caracteres de salida adicionales, se establece un valor en *estado*, de modo que las llamadas posteriores a la función generan los caracteres adicionales y devuelven el valor -3. Si no se requieren más caracteres de salida, *el estado* se establece en el estado de desplazamiento inicial.

Para convertir caracteres multibyte no UTF-8 a caracteres LE UTF-16, utilice las funciones [mbrtowc](mbrtowc.md), [mbtowc o _mbtowc_l.](mbtowc-mbtowc-l.md)

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**mbrtoc16**, **mbrtoc32**|\<uchar.h>|\<cuchar>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../compatibility.md).

## <a name="see-also"></a>Consulte también

[Conversión de datos](../data-conversion.md)\
[Configuración regional](../locale.md)\
[Interpretación de secuencias multibyte-carácter](../interpretation-of-multibyte-character-sequences.md)\
[c16rtomb, c32rtomb](c16rtomb-c32rtomb1.md)\
[mbrtowc](mbrtowc.md)\
[mbsrtowcs](mbsrtowcs.md)\
[mbsrtowcs_s](mbsrtowcs-s.md)
