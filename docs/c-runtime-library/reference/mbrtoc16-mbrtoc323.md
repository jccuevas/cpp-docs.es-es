---
title: mbrtoc16, mbrtoc323 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- mbrtoc16
- mbrtoc32
apilocation:
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
apitype: DLLExport
f1_keywords:
- mbrtoc16
- mbrtoc32
- uchar/mbrtoc16
- uchar/mbrtoc32
dev_langs:
- C++
helpviewer_keywords:
- mbrtoc16 function
- mbrtoc32 function
ms.assetid: 099ade4d-56f7-4e61-8b45-493f1d7a64bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a12e90f9a4bc0cc27df421c27d77a1b9b69334b9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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

*Destino*<br/>
Puntero a la **char16_t** o **char32_t** equivalente del carácter multibyte a convertir. Si es null, la función no almacena un valor.

*Origen*<br/>
Puntero a la cadena de caracteres multibyte que se va a convertir.

*max_bytes*<br/>
El número máximo de bytes de *origen* a examinar para que el carácter que se va a convertir. Esto debe ser un valor entre 1 y el número de bytes, incluidos los terminadores null, permanecen en *origen*.

*state*<br/>
Puntero a un **mbstate_t** objeto de estado de conversión utilizado para interpretar la cadena multibyte en uno o más caracteres de salida.

## <a name="return-value"></a>Valor devuelto

Si se ejecuta correctamente, devuelve el valor de la primera de estas condiciones que se aplica, dado el actual *estado* valor:

|Valor|Condición|
|-----------|---------------|
|0|La siguiente *max_bytes* o menos caracteres convertidos de *origen* se corresponden con el carácter ancho nulo, que es el valor almacenado si *destino* no es null.<br /><br /> *estado* contiene el estado de desplazamiento inicial.|
|Entre 1 y *max_bytes*, ambos inclusive|El valor devuelto es el número de bytes de *origen* que completan un carácter multibyte válido. El carácter ancho convertido se almacena si *destino* no es null.|
|-3|El siguiente carácter ancho resultante de una llamada anterior a la función se ha almacenado en *destino* si *destino* no es null. Ningún byte de *origen* son consumidos por esta llamada a la función.<br /><br /> Cuando *origen* apunta a un carácter multibyte que requiere más de un carácter ancho para representar (por ejemplo, un par suplente), el *estado* valor se actualiza para que escribe la siguiente llamada de función  el carácter adicional.|
|-2|La siguiente *max_bytes* bytes representan un incompleto pero potencialmente válido de carácter multibyte. Ningún valor se almacena en *destino*. Este resultado se puede producir si *max_bytes* es cero.|
|-1|Se ha producido un error de codificación. La siguiente *max_bytes* o menos bytes no contribuyen a un carácter multibyte completo y válido. Ningún valor se almacena en *destino*.<br /><br /> **EILSEQ** se almacena en **errno** y el estado de la conversión *estado* no está especificado.|

## <a name="remarks"></a>Comentarios

El **mbrtoc16** función lee hasta *max_bytes* bytes a partir de *origen* para buscar el primer carácter multibyte completo y válido y, a continuación, almacena el equivalente UTF-16 carácter de *destino*. Los bytes de origen se interpretan según la configuración regional multibyte de subprocesos actual. Si el carácter multibyte requiere más de un carácter de salida UTF-16, como un par suplente, el *estado* valor está configurado para almacenar el siguiente carácter UTF-16 en *destino* en la siguiente llamada a **mbrtoc16**. El **mbrtoc32** función es idéntica, pero el resultado se almacena como un carácter UTF-32.

Si *origen* es null, estas funciones devuelven el equivalente de una llamada realizada con argumentos de **NULL** para *destino*, **""** para *origen*y 1 para *max_bytes*. Los valores pasados de *destino* y *max_bytes* se omiten.

Si *origen* es no es null, la función comienza al principio de la cadena e inspecciona hasta *max_bytes* bytes para determinar el número de bytes necesarios para completar el siguiente carácter multibyte, incluidas las secuencias de desplazamiento. Si los bytes examinados contienen un carácter multibyte válido y completo, la función convierte el carácter en los caracteres anchos equivalentes de 16 o 32 bits. Si *destino* no es nulo, la función almacena el resultado de la primero (y posiblemente único) de caracteres de destino. Si se requieren caracteres de salida adicionales, se establece un valor *estado*, de modo que las llamadas subsiguientes a la función generen los caracteres adicionales y devuelven el valor -3. Si no hay más caracteres de salida son necesarios, a continuación, *estado* se establece en el estado de desplazamiento inicial.

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
