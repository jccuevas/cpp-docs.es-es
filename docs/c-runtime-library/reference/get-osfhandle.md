---
title: _get_osfhandle
ms.date: 4/2/2020
api_name:
- _get_osfhandle
- _o__get_osfhandle
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
- get_osfhandle
- _get_osfhandle
helpviewer_keywords:
- operating systems, getting file handles
- get_osfhandle function
- _get_osfhandle function
- file handles [C++], operating system
ms.assetid: 0bdd728a-4fd8-410b-8c9f-01a121135196
ms.openlocfilehash: a12c0c93ae15350a4b91a8aa905acb941f8b6a10
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345032"
---
# <a name="_get_osfhandle"></a>_get_osfhandle

Recupera el identificador de archivo del sistema operativo asociado al descriptor de archivo especificado.

## <a name="syntax"></a>Sintaxis

```C
intptr_t _get_osfhandle(
   int fd
);
```

### <a name="parameters"></a>Parámetros

*Fd*<br/>
Descriptor del archivo existente.

## <a name="return-value"></a>Valor devuelto

Devuelve un identificador de archivo del sistema operativo si *fd* es válido. De lo contrario, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, devuelve **INVALID_HANDLE_VALUE** (-1). También establece **errno en** **EBADF**, lo que indica un identificador de archivo no válido. Para evitar una advertencia cuando el resultado se utiliza como identificador de archivo Win32, conviéstelo a un tipo **HANDLE.**

> [!NOTE]
> Cuando **stdin**, **stdout**y **stderr** no están asociados a una secuencia (por ejemplo, en una aplicación de Windows sin una ventana de consola), los valores descriptores de archivo para estas secuencias se devuelven de [_fileno](fileno.md) como el valor especial -2. De forma similar, si utiliza un parámetro de descriptor de archivo 0, 1 o 2 en lugar del resultado de una llamada a **_fileno**, **_get_osfhandle** también devuelve el valor especial -2 cuando el descriptor de archivo no está asociado a una secuencia y no establece **errno**. Sin embargo, esto no es un valor de identificador de archivo válido y es probable que se produzcaun un error en las llamadas posteriores que intentan usarlo.

Para obtener más información acerca de **EBADF** y otros códigos de error, consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Observaciones

Para cerrar un archivo cuyo identificador de archivo de sistema operativo (SO) se obtiene **mediante _get_osfhandle**, llame a [_close](close.md) en el descriptor de archivo *fd*. Nunca llame a **CloseHandle** en el valor devuelto de esta función. El identificador de archivo del sistema operativo subyacente es propiedad del descriptor de archivo *fd* y se cierra cuando se llama [a _close](close.md) en *fd*. Si el descriptor de `FILE *` archivo es propiedad de `FILE *` una secuencia, al llamar a [fclose](fclose-fcloseall.md) en esa secuencia se cierra nalto del descriptor de archivo y del identificador de archivo del sistema operativo subyacente. En este caso, no llame a [_close](close.md) en el descriptor de archivo.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_get_osfhandle**|\<io.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[\_open_osfhandle](open-osfhandle.md)
