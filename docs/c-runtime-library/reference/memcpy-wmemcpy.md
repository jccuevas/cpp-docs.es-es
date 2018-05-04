---
title: memcpy, wmemcpy | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- memcpy
- wmemcpy
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
apitype: DLLExport
f1_keywords:
- wmemcpy
- memcpy
dev_langs:
- C++
helpviewer_keywords:
- wmemcpy function
- memcpy function
ms.assetid: 34abb90b-bffb-46dc-a2f3-a5e9940839d6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a9880bdbc608933a1b6cfffe3473a9b07f0252ae
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="memcpy-wmemcpy"></a>memcpy, wmemcpy

Copia bytes entre búferes. Hay disponibles versiones más seguras de estas funciones; vea [memcpy_s, wmemcpy_s](memcpy-s-wmemcpy-s.md).

## <a name="syntax"></a>Sintaxis

```C
void *memcpy(
   void *dest,
   const void *src,
   size_t count
);
wchar_t *wmemcpy(
   wchar_t *dest,
   const wchar_t *src,
   size_t count
);
```

### <a name="parameters"></a>Parámetros

*dest*<br/>
Nuevo búfer.

*src*<br/>
Búfer del que copiar.

*count*<br/>
Número de caracteres que se copiará.

## <a name="return-value"></a>Valor devuelto

El valor de *dest*.

## <a name="remarks"></a>Comentarios

**memcpy** copias *recuento* bytes a partir de *src* a *dest*; **wmemcpy** copias *recuento* caracteres anchos (dos bytes). Si el origen y destino se superponen, el comportamiento de **memcpy** no está definido. Use **memmove** para controlar las áreas superpuestas.

> [!IMPORTANT]
> Asegúrese de que el búfer de destino sea del mismo tamaño o mayor que el búfer de origen. Para obtener más información, vea [Avoiding Buffer Overruns](http://msdn.microsoft.com/library/windows/desktop/ms717795)(Evitar saturaciones del búfer).

> [!IMPORTANT]
> Dado que se realiza un seguimiento de por lo que muchas saturaciones del búfer y posibles vulnerabilidades de seguridad para un uso inapropiado de **memcpy**, esta función se cuenta entre las "prohibidas" por el ciclo de vida de desarrollo de seguridad (SDL).  Se puede observar que algunas clases de biblioteca de VC ++ seguirán usando **memcpy**.  Además, puede observar que el optimizador del compilador de VC ++ emite en ocasiones llamadas a **memcpy**.  El producto Visual C++ se desarrolla de acuerdo con el proceso SDL, por lo que se ha evaluado con cuidado el uso de esta función prohibida.  En el caso de su uso por parte de bibliotecas, se han examinado meticulosamente las llamadas para garantizar que no provoquen saturaciones de búferes.  En el caso del compilador, determinados patrones de código se reconocen en ocasiones como idénticos al patrón de **memcpy**y por tanto se reemplazan con una llamada a la función.  En tales casos, el uso de **memcpy** no es menos seguro que no sea el original habría sido instrucciones; simplemente se han optimizado para una llamada a rendimiento ajustado **memcpy** función.  Al igual que el uso de funciones de CRT "seguras" no garantiza la seguridad (solo dificulta la falta de seguridad), el uso de funciones "prohibidas" no garantiza el peligro (solo se requiere un mayor escrutinio para garantizar la seguridad).
>
> Dado que **memcpy** uso por el compilador de VC ++ y bibliotecas está tan estudiado, se permiten estas llamadas dentro del código en caso contrario, es la conformidad con SDL.  **memcpy** llamadas introducidas en el código fuente de aplicación solo son conformes a SDL si ese han revisado expertos en seguridad.

El **memcpy** y **wmemcpy** funciones solo quedarán desusadas si la constante **_CRT_SECURE_DEPRECATE_MEMORY** se define antes de la declaración de inclusión en orden para las funciones en desuso, como en el ejemplo siguiente:

```C
#define _CRT_SECURE_DEPRECATE_MEMORY
#include <memory.h>
```

o

```C
#define _CRT_SECURE_DEPRECATE_MEMORY
#include <wchar.h>
```

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**memcpy**|\<memory.h> o \<string.h>|
|**wmemcpy**|\<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea [memmove](memmove-wmemmove.md) para obtener un ejemplo de cómo usar **memcpy**.

## <a name="see-also"></a>Vea también

[Manipulación del búfer](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memchr, wmemchr](memchr-wmemchr.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[memmove, wmemmove](memmove-wmemmove.md)<br/>
[memset, wmemset](memset-wmemset.md)<br/>
[strcpy_s, wcscpy_s, _mbscpy_s](strcpy-s-wcscpy-s-mbscpy-s.md)<br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
