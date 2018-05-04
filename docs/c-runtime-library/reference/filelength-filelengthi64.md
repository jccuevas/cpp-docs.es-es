---
title: _filelength, _filelengthi64 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _filelengthi64
- _filelength
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
- _filelength
- _filelengthi64
- filelengthi64
dev_langs:
- C++
helpviewer_keywords:
- filelengthi64 function
- lengths, file
- filelength function
- _filelength function
- files [C++], length
- _filelengthi64 function
ms.assetid: 3ab83d5a-543c-4079-b9d9-0abfc7da0275
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 33943eb81658b065116d30592f25ef004d4bfc1b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="filelength-filelengthi64"></a>_filelength, _filelengthi64

Obtiene la longitud de un archivo.

## <a name="syntax"></a>Sintaxis

```C
long _filelength(
   int fd
);
__int64 _filelengthi64(
   int fd
);
```

### <a name="parameters"></a>Parámetros

*FD*<br/>
Se destina al descriptor de archivo.

## <a name="return-value"></a>Valor devuelto

Ambos **_filelength** y **_filelengthi64** devolver la longitud del archivo, en bytes, del archivo de destino asociado con *fd*. Si *fd* es un descriptor de archivo no válido, esta función invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, ambas funciones devuelven-1 L para indicar un error y establecer **errno** a **EBADF**.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**_filelength**|\<io.h>|
|**_filelengthi64**|\<io.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Consulte el ejemplo de [_chsize](chsize.md).

## <a name="see-also"></a>Vea también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
[_chsize](chsize.md)<br/>
[_fileno](fileno.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_stat, _wstat (Funciones)](stat-functions.md)<br/>
[_stat, _wstat (Funciones)](stat-functions.md)<br/>
