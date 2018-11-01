---
title: _setmaxstdio
ms.date: 11/04/2016
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
helpviewer_keywords:
- maximum open files
- _setmaxstdio function
- setmaxstdio function
- open files, maximum
ms.assetid: 9e966875-9ff5-47c4-9b5f-e79e83b70249
ms.openlocfilehash: 58cffedf673e23a69c2d8040071b2e3353ff4502
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445089"
---
# <a name="setmaxstdio"></a>_setmaxstdio

Establece un valor máximo para el número de archivos abiertos simultáneamente en el **stdio** nivel.

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

Devuelve *newmax* si se realiza correctamente; en caso contrario, de -1.

Si *newmax* es menor que **_IOB_ENTRIES** o mayor, a continuación, se invoca el número máximo de controladores disponibles en el sistema operativo, el controlador de parámetros no válidos, como se describe en [ Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función devuelve -1 y establece **errno** a **EINVAL**.

Para obtener información sobre estos y otros códigos de error, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

El **_setmaxstdio** función cambia el valor máximo para el número de archivos que se pueden abrir simultáneamente en el **stdio** nivel.

La E/S en tiempo de ejecución de C ahora admite muchos más archivos abiertos en las plataformas de Win32 que en las versiones anteriores. Hasta 2048 archivos puede estar abierto simultáneamente en el [nivel de lowio](../../c-runtime-library/low-level-i-o.md) (es decir, puede abrir y acceso por medio de la **_open**, **_read**, **_write**, y así sucesivamente familia de funciones de E/S). Hasta 512 archivos puede estar abierto simultáneamente en el [nivel de stdio](../../c-runtime-library/stream-i-o.md) (es decir, puede abrir y acceso por medio de la **fopen**, **fgetc**, **fputc** y así sucesivamente familia de funciones). El límite de 512 archivos abiertos en el **stdio** nivel se puede aumentar hasta un máximo de 2048 mediante la **_setmaxstdio** función.

Dado que **stdio**-las funciones de nivel, como **fopen**, se crean en la parte superior de la **lowio** functions, el máximo de 2048 es un límite superior para el número de forma simultánea Abra los archivos que se tiene acceso a través de la biblioteca de tiempo de ejecución de C.

> [!NOTE]
> Este límite superior puede exceder la compatibilidad de ciertas plataformas y configuraciones de Win32.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_setmaxstdio**|\<stdio.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Consulte [_getmaxstdio](getmaxstdio.md) para obtener un ejemplo del uso de **_setmaxstdio**.

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
