---
title: _chsize_s
ms.date: 4/2/2020
api_name:
- _chsize_s
- _o__chsize_s
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- chsize_s
- _chsize_s
helpviewer_keywords:
- files [C++], changing size
- chsize_s function
- _chsize_s function
ms.assetid: d88d2e94-6e3b-42a5-8631-16ac4d82fa38
ms.openlocfilehash: 70845124eb889d73a0f87aadd923e2d86db96c29
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350082"
---
# <a name="_chsize_s"></a>_chsize_s

Cambia el tamaño de un archivo. Se trata de una versión de [_chsize](chsize.md) con mejoras de seguridad, tal y como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t _chsize_s(
   int fd,
   __int64 size
);
```

### <a name="parameters"></a>Parámetros

*Fd*<br/>
Descriptor de archivo que hace referencia a un archivo abierto.

*Tamaño*<br/>
Nueva longitud del archivo en bytes.

## <a name="return-value"></a>Valor devuelto

**_chsize_s** devuelve el valor 0 si el tamaño del archivo se ha cambiado correctamente. Un valor devuelto distinto de cero indica un error: el valor devuelto es **EACCES** si el archivo especificado está bloqueado contra el acceso, **EBADF** si el archivo especificado es de solo lectura o el descriptor no es válido, **ENOSPC** si no queda espacio en el dispositivo, o **EINVAL** si el tamaño es menor que cero. **errno** se establece en el mismo valor.

Para obtener más información sobre estos y otros códigos de retorno, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Observaciones

La función **_chsize_s** extiende o trunca el archivo asociado a *fd* a la longitud especificada por *size*. El archivo debe estar abierto en un modo que permita escritura. Si el archivo se amplía, se anexan caracteres nulos ("\0"). Si el archivo se trunca, se pierden todos los datos desde el final del archivo abreviado hasta la longitud original del archivo.

**_chsize_s** toma un entero de 64 bits como tamaño de archivo y, por lo tanto, puede controlar tamaños de archivo superiores a 4 GB. **_chsize** está limitada a tamaños de archivo de 32 bits.

Esta función valida sus parámetros. Si *fd* no es un descriptor de archivo válido o el tamaño es menor que cero, se invoca el controlador de parámetros no válidos, como se describe en [validación](../../c-runtime-library/parameter-validation.md)de parámetros .

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_chsize_s**|\<io.h>|\<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
[_chsize](chsize.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
