---
title: _get_osfhandle | Microsoft Docs
ms.custom: 
ms.date: 12/12/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4ffc65e12c4a9023d0ef649bbf2cb5e8f7e76808
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="getosfhandle"></a>_get_osfhandle

Recupera el identificador de archivo del sistema operativo asociado al descriptor de archivo especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
intptr_t _get_osfhandle(   
   int fd   
);  
```  
  
### <a name="parameters"></a>Parámetros

*fd*  
Descriptor del archivo existente.  
  
## <a name="return-value"></a>Valor devuelto

Devuelve un identificador de archivo del sistema operativo si *fd* es válida. De lo contrario, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función devuelve `INVALID_HANDLE_VALUE` (-1) y establece `errno` a `EBADF`, que indica un identificador de archivo no válido.  
  
## <a name="remarks"></a>Comentarios

Para cerrar un archivo cuyo identificador de archivos del sistema operativo (SO) se obtiene mediante `_get_osfhandle`, llame a [ \_cerrar](../../c-runtime-library/reference/close.md) en el descriptor de archivo *fd*. No llame a `CloseHandle` en el valor devuelto de esta función. El identificador de archivo del sistema operativo subyacente pertenece a la *fd* descriptor de archivo y se cierra cuando `_close` se llama en *fd*. Si el descriptor de archivo pertenece a un `FILE *` secuencia, a continuación, llamar a [fclose](../../c-runtime-library/reference/fclose-fcloseall.md) en ese `FILE *` secuencia cierra el descriptor de archivo y el identificador de archivo del sistema operativo subyacente. En este caso, no llame a `_close` en el descriptor de archivo.
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_get_osfhandle`|\<io.h>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="see-also"></a>Vea también

[Control de archivos](../../c-runtime-library/file-handling.md)   
[_close](../../c-runtime-library/reference/close.md)   
[_creat, _wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
[_dup, _dup2](../../c-runtime-library/reference/dup-dup2.md)   
[_open, _wopen](../../c-runtime-library/reference/open-wopen.md)
