---
title: _get_osfhandle | Microsoft Docs
ms.custom: 
ms.date: 09/11/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _get_osfhandle
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
dev_langs: C++
helpviewer_keywords:
- operating systems, getting file handles
- get_osfhandle function
- _get_osfhandle function
- file handles [C++], operating system
ms.assetid: 0bdd728a-4fd8-410b-8c9f-01a121135196
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4e3b15b4577d1d8c0b24df82acff76494474c4e6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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

*FD* descriptor del archivo existente.  
  
## <a name="return-value"></a>Valor devuelto

Identificador de un archivo de sistema operativo si *fd* es válida. De lo contrario, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función devuelve `INVALID_HANDLE_VALUE` (-1) y establece `errno` a `EBADF`, que indica un identificador de archivo no válido.  
  
## <a name="remarks"></a>Comentarios

Para cerrar un archivo cuyo identificador de archivo del sistema operativo se obtiene mediante `_get_osfhandle`, llame a [ \_cerrar](../../c-runtime-library/reference/close.md) en el descriptor de archivo *fd*. El identificador subyacente también se cierra mediante una llamada a `_close`, por lo que no es necesario llamar a la función `CloseHandle` de Win32 en el identificador original.  
  
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
