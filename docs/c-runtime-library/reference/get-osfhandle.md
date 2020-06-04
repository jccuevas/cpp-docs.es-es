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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 085bf20a12d9b77be0977521bde2ab75d9b2636a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918284"
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

*FD*<br/>
Descriptor del archivo existente.

## <a name="return-value"></a>Valor devuelto

Devuelve un identificador de archivo del sistema operativo Si *FD* es válido. De lo contrario, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, devuelve **INVALID_HANDLE_VALUE** (-1). También establece **errno** en **EBADF**, lo que indica un identificador de archivo no válido. Para evitar una advertencia cuando el resultado se utiliza como identificador de archivo de Win32, conviértalo en un tipo de **identificador** .

> [!NOTE]
> Cuando **stdin**, **stdout**y **stderr** no están asociados a un flujo (por ejemplo, en una aplicación de Windows sin una ventana de consola), los valores de descriptor de archivo para estos flujos se devuelven desde [_fileno](fileno.md) como valor especial 2. Del mismo modo, si usa 0, 1 o 2 como parámetro de descriptor de archivo en lugar del resultado de una llamada a **_fileno**, **_get_osfhandle** también devuelve el valor especial 2 cuando el descriptor de archivo no está asociado a una secuencia y no establece **errno**. Sin embargo, este no es un valor de identificador de archivo válido y es probable que se produzcan errores en las llamadas subsiguientes que intenten usarlo.

Para obtener más información sobre **EBADF** y otros códigos de error, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Observaciones

Para cerrar un archivo cuyo identificador de archivo del sistema operativo (SO) obtiene **_get_osfhandle**, llame a [_close](close.md) en el archivo *FD*del descriptor de archivo. Nunca llame a **CloseHandle** en el valor devuelto de esta función. El identificador de archivo del sistema operativo subyacente es propiedad del descriptor de archivo *FD* y se cierra cuando se llama a [_close](close.md) en *FD*. Si el descriptor de archivo es `FILE *` propiedad de una secuencia, al llamar `FILE *` a [fclose](fclose-fcloseall.md) en esa secuencia se cierra el descriptor de archivo y el identificador de archivo del sistema operativo subyacente. En este caso, no llame a [_close](close.md) en el descriptor de archivo.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_get_osfhandle**|\<io.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulta también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[\_open_osfhandle](open-osfhandle.md)
