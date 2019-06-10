---
title: _get_osfhandle
ms.date: 05/29/2018
apiname:
- _get_osfhandle
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
- get_osfhandle
- _get_osfhandle
helpviewer_keywords:
- operating systems, getting file handles
- get_osfhandle function
- _get_osfhandle function
- file handles [C++], operating system
ms.assetid: 0bdd728a-4fd8-410b-8c9f-01a121135196
ms.openlocfilehash: cc3b50e3d3f65bee83b8df83aa0adb5c8694e35a
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821663"
---
# <a name="getosfhandle"></a>_get_osfhandle

Recupera el identificador de archivo del sistema operativo asociado al descriptor de archivo especificado.

## <a name="syntax"></a>Sintaxis

```C
intptr_t _get_osfhandle(
   int fd
);
```

### <a name="parameters"></a>Parámetros

*fd*<br/>
Descriptor del archivo existente.

## <a name="return-value"></a>Valor devuelto

Devuelve un identificador de archivo del sistema operativo si *fd* es válido. De lo contrario, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, devuelve **INVALID_HANDLE_VALUE** (-1). También establece **errno** a **EBADF**, que indica un identificador de archivo no válido. Para evitar una advertencia cuando el resultado se utiliza como un identificador de archivo Win32, conviértalo a un **controlar** tipo.

> [!NOTE]
> Cuando **stdin**, **stdout**, y **stderr** no están asociados a una secuencia (por ejemplo, en una aplicación de Windows sin una ventana de consola), los valores del descriptor de archivo para Estas secuencias se devuelven desde [_fileno](fileno.md) como especial valor -2. De forma similar, si usa un 0, 1 o 2 como el parámetro del descriptor de archivo en lugar del resultado de una llamada a **_fileno**, **_get_osfhandle** también devuelve el valor especial -2 cuando el descriptor de archivo no está asociado con una secuencia y no establece **errno**. Sin embargo, esto no es un valor de identificador de archivo válido y las llamadas subsiguientes que intentan usar, están probables que den.

Para obtener más información acerca de **EBADF** y otros códigos de error, consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

Para cerrar un archivo cuyo identificador de archivo del sistema operativo (SO) se obtiene mediante **_get_osfhandle**, llame a [_close](close.md) en el descriptor de archivo *fd*. Nunca se llame a **CloseHandle** en el valor devuelto de esta función. El identificador de archivo del sistema operativo subyacente pertenece a la *fd* descriptor de archivo y se cierra cuando [_close](close.md) se llama en *fd*. Si el descriptor de archivo pertenece a un `FILE *` secuencia, a continuación, llamar a [fclose](fclose-fcloseall.md) en que `FILE *` secuencia cierra el descriptor de archivo y el identificador de archivo del sistema operativo subyacente. En este caso, no llame a [_close](close.md) en el descriptor de archivo.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_get_osfhandle**|\<io.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[\_open_osfhandle](open-osfhandle.md)
