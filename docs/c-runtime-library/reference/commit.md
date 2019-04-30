---
title: _commit
ms.date: 11/04/2016
apiname:
- _commit
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
- _commit
- commit
helpviewer_keywords:
- files [C++], flushing
- flushing files to disk
- commit function
- _commit function
- committing files to disk
ms.assetid: d0c74d3a-4f2d-4fb0-b140-2d687db3d233
ms.openlocfilehash: 8408158cb3d4ef0d29d9af24d8a2acbd28e00192
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62340364"
---
# <a name="commit"></a>_commit

Vacía el contenido de un archivo directamente en el disco.

## <a name="syntax"></a>Sintaxis

```C
int _commit(
   int fd
);
```

### <a name="parameters"></a>Parámetros

*fd*<br/>
Descriptor de archivo que hace referencia al archivo abierto.

## <a name="return-value"></a>Valor devuelto

**_confirmar** devuelve 0 si el archivo correctamente se vacía en el disco. Un valor devuelto de -1 indica un error.

## <a name="remarks"></a>Comentarios

El **_confirmar** función fuerza el sistema operativo para escribir el archivo asociado *fd* en el disco. Esta llamada se asegura de que el archivo especificado se vacíe inmediatamente, no a discreción del sistema operativo.

Si *fd* es un descriptor de archivo no válido, se invoca el controlador de parámetros no válidos, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve -1 y **errno** está establecido en **EBADF**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezados opcionales|
|-------------|---------------------|----------------------|
|**_commit**|\<io.h>|\<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[E/S de bajo nivel](../../c-runtime-library/low-level-i-o.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_read](read.md)<br/>
[_write](write.md)<br/>
