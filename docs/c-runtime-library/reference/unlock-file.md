---
title: _unlock_file | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _unlock_file
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _unlock_file
- unlock_file
dev_langs: C++
helpviewer_keywords:
- files [C++], unlocking
- unlock_file function
- _unlock_file function
- unlocking files
ms.assetid: cf380a51-6d3a-4f38-bd64-2d4fb57b4369
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 246fd73cdc3b380dae7ea9a6a3d02fcd9290ba1d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="unlockfile"></a>_unlock_file
Desbloquea un archivo para que otros procesos puedan acceder a él.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void _unlock_file(  
   FILE* file  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `file`  
 Identificador de archivo.  
  
## <a name="remarks"></a>Comentarios  
 La función `_unlock_file` desbloquea el archivo especificado por `file`. El desbloqueo de un archivo permite que otros procesos accedan a él. No se debe llamar a esta función, a menos que previamente se haya llamado a `_lock_file` en el puntero `file`. La llamada a `_unlock_file` en un archivo que no está bloqueado puede provocar un interbloqueo. A modo de ejemplo, vea [_lock_file](../../c-runtime-library/reference/lock-file.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_unlock_file`|\<stdio.h>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="see-also"></a>Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)   
 [_creat, _wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [_open, _wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_lock_file](../../c-runtime-library/reference/lock-file.md)