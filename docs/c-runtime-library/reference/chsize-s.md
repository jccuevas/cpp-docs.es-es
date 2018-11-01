---
title: _chsize_s
ms.date: 11/04/2016
apiname:
- _chsize_s
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
- chsize_s
- _chsize_s
helpviewer_keywords:
- files [C++], changing size
- chsize_s function
- _chsize_s function
ms.assetid: d88d2e94-6e3b-42a5-8631-16ac4d82fa38
ms.openlocfilehash: a56efe826d43c80dc2cdee295e58872e7dd3c9ea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50597605"
---
# <a name="chsizes"></a>_chsize_s

Cambia el tamaño de un archivo. Se trata de una versión de [_chsize](chsize.md) con mejoras de seguridad, tal y como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t _chsize_s(
   int fd,
   __int64 size
);
```

### <a name="parameters"></a>Parámetros

*FD*<br/>
Descriptor de archivo que hace referencia a un archivo abierto.

*size*<br/>
Nueva longitud del archivo en bytes.

## <a name="return-value"></a>Valor devuelto

**_chsize_s** devuelve el valor 0 si el tamaño del archivo se cambió correctamente. Un valor devuelto distinto de cero indica un error: el valor devuelto es **EACCES** si el archivo especificado está bloqueado contra el acceso, **EBADF** si el archivo especificado es de solo lectura o no es válido, el descriptor de **ENOSPC** si no se queda espacio en el dispositivo, o **EINVAL** si el tamaño es menor que cero. **errno** se establece en el mismo valor.

Para obtener más información sobre estos y otros códigos de retorno, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

El **_chsize_s** función amplía o trunca el archivo asociado *fd* a la longitud especificada por *tamaño*. El archivo debe estar abierto en un modo que permita escritura. Si el archivo se amplía, se anexan caracteres nulos ("\0"). Si el archivo se trunca, se pierden todos los datos desde el final del archivo abreviado hasta la longitud original del archivo.

**_chsize_s** toma un entero de 64 bits como el tamaño del archivo y, por lo tanto, puede controlar tamaños de archivo mayores que 4 GB. **_chsize** se limita al tamaño de los archivos de 32 bits.

Esta función valida sus parámetros. Si *fd* no es un descriptor de archivo válido o el tamaño es menor que cero, se invoca el controlador de parámetros no válidos, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_chsize_s**|\<io.h>|\<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
[_chsize](chsize.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
