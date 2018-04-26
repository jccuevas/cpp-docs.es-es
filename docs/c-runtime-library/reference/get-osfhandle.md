---
title: _get_osfhandle | Microsoft Docs
ms.custom: ''
ms.date: 12/12/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- operating systems, getting file handles
- get_osfhandle function
- _get_osfhandle function
- file handles [C++], operating system
ms.assetid: 0bdd728a-4fd8-410b-8c9f-01a121135196
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ef9481cb0ad962de96b710b31ac1460b9703ae6e
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
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

*FD*<br/>
Descriptor del archivo existente.

## <a name="return-value"></a>Valor devuelto

Devuelve un identificador de archivo del sistema operativo si *fd* es válida. De lo contrario, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función devuelve **INVALID_HANDLE_VALUE** (-1) y establece **errno** a **EBADF**, que indica un identificador de archivo no válido.

## <a name="remarks"></a>Comentarios

Para cerrar un archivo cuyo identificador de archivos del sistema operativo (SO) se obtiene mediante **_get_osfhandle**, llame a [_close](close.md) en el descriptor de archivo *fd*. No llame a **CloseHandle** en el valor devuelto de esta función. El identificador de archivo del sistema operativo subyacente pertenece a la *fd* descriptor de archivo y se cierra cuando [_close](close.md) se llama en *fd*. Si el descriptor de archivo pertenece a un **archivo \***  secuencia, a continuación, llamar a [fclose](fclose-fcloseall.md) en ese **archivo \***  secuencia cierra el descriptor de archivo y el identificador de archivo de sistema operativo subyacente. En este caso, no llame a [_close](close.md) en el descriptor de archivo.

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
