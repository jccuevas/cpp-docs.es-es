---
title: _setmaxstdio
ms.date: 05/21/2019
api_name:
- _setmaxstdio
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- setmaxstdio
- _setmaxstdio
helpviewer_keywords:
- maximum open files
- _setmaxstdio function
- setmaxstdio function
- open files, maximum
ms.assetid: 9e966875-9ff5-47c4-9b5f-e79e83b70249
ms.openlocfilehash: 620213b4df9ea555189a1403b3c9e83b55cad6c6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948219"
---
# <a name="_setmaxstdio"></a>_setmaxstdio

Establece el número de archivos que se permite abrir simultáneamente en el nivel de flujo de E/S.

## <a name="syntax"></a>Sintaxis

```C
int _setmaxstdio(
   int new_max
);
```

### <a name="parameters"></a>Parámetros

*new_max*<br/>
Nuevo número de archivos que se permite abrir simultáneamente en el nivel de flujo de E/S.

## <a name="return-value"></a>Valor devuelto

Devuelve *new_max* si se realiza correctamente; en caso contrario, devuelve -1.

Si *new_max* es menor que **_IOB_ENTRIES** o mayor que el número máximo de controladores disponibles en el sistema operativo, se invoca al controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función devuelve -1 y establece **errno** en **EINVAL**.

Para obtener información sobre estos y otros códigos de error, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

La función **_setmaxstdio** cambia el valor máximo del número de archivos que pueden estar abiertos simultáneamente en el nivel de flujo de E/S.

La E/S de tiempo de ejecución de C ahora admite hasta 8192 archivos abiertos simultáneamente en el nivel de [flujo de E/S inferior](../../c-runtime-library/low-level-i-o.md). Este nivel incluye los archivos abiertos y aquellos a los que se ha accedido mediante la familia de funciones de E/S **_open**, **_read** y **_write**. De forma predeterminada, se pueden abrir hasta 512 archivos al mismo tiempo en el nivel de [flujo de E/S](../../c-runtime-library/stream-i-o.md). Este nivel incluye los archivos abiertos y aquellos a los que se ha accedido mediante la familia de funciones **fopen**, **fgetc** y **fputc**. El límite de 512 archivos abiertos en el nivel de flujo de E/S se puede aumentar hasta un máximo de 8192 mediante la función **_setmaxstdio**.

Dado que las funciones de nivel de flujo de E/S (como **fopen**) se crean a partir de las funciones de nivel de flujo de E/S, el máximo de 8192 archivos es un límite superior para el número de archivos abiertos simultáneamente a los que se obtiene acceso a través de la biblioteca de tiempo de ejecución de C.

> [!NOTE]
> Este límite superior puede exceder los valores que admiten ciertas plataformas y configuraciones de Win32.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_setmaxstdio**|\<stdio.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea [_getmaxstdio](getmaxstdio.md) para obtener un ejemplo del uso de **_setmaxstdio**.

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
