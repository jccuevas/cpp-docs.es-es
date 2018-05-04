---
title: _setmaxstdio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _setmaxstdio
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- setmaxstdio
- _setmaxstdio
dev_langs:
- C++
helpviewer_keywords:
- maximum open files
- _setmaxstdio function
- setmaxstdio function
- open files, maximum
ms.assetid: 9e966875-9ff5-47c4-9b5f-e79e83b70249
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 785fcc05c6b19086c14edc85983749894c867c18
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="setmaxstdio"></a>_setmaxstdio

Establece el número de archivos abiertos simultáneamente en el **stdio** nivel.

## <a name="syntax"></a>Sintaxis

```C
int _setmaxstdio(
   int newmax
);
```

### <a name="parameters"></a>Parámetros

*newmax*<br/>
Nuevo máximo para el número de archivos abiertos simultáneamente en el **stdio** nivel.

## <a name="return-value"></a>Valor devuelto

Devuelve *newmax* si se realiza correctamente; en caso contrario de -1.

Si *newmax* es menor que **_IOB_ENTRIES** o superior, a continuación, se invoca el número máximo de identificadores disponibles en el sistema operativo, el controlador de parámetros no válidos, tal y como se describe en [ Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función devuelve -1 y establece **errno** a **EINVAL**.

Para obtener información sobre estos y otros códigos de error, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

El **_setmaxstdio** función cambia el valor máximo para el número de archivos que pueden abrir simultáneamente en el **stdio** nivel.

La E/S en tiempo de ejecución de C ahora admite muchos más archivos abiertos en las plataformas de Win32 que en las versiones anteriores. Hasta 2.048 archivos puede estar abierto simultáneamente en el [lowio nivel](../../c-runtime-library/low-level-i-o.md) (es decir, abierto y tiene acceso por medio de la **_open**, **_preguntas**, **_write**, y así sucesivamente familia de funciones de E/S). Hasta 512 archivos puede estar abierto simultáneamente en el [nivel stdio](../../c-runtime-library/stream-i-o.md) (es decir, abierto y tiene acceso por medio de la **fopen**, **fgetc**, **fputc** y así sucesivamente familia de funciones). El límite de 512 archivos abiertos en el **stdio** nivel se puede aumentar hasta un máximo de 2048 por medio de la **_setmaxstdio** (función).

Dado que **stdio**-nivel de funciones, como **fopen**, se generan en la parte superior de la **lowio** funciones, el número máximo de 2.048 es un límite superior para el número de simultáneamente abrir archivos que se tiene accesibles a través de la biblioteca de tiempo de ejecución de C.

> [!NOTE]
> Este límite superior puede exceder la compatibilidad de ciertas plataformas y configuraciones de Win32.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_setmaxstdio**|\<stdio.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea [_getmaxstdio](getmaxstdio.md) para obtener un ejemplo del uso de **_setmaxstdio**.

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
