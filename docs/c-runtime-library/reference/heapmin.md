---
title: _heapmin | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _heapmin
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _heapmin
- heapmin
dev_langs:
- C++
helpviewer_keywords:
- heap memory
- minimizing heaps
- memory, releasing
- heaps, releasing unused memory
- _heapmin function
- heapmin function
ms.assetid: c0bccdf6-2d14-4d7b-a7ff-d6a17bdb410f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 986d56560b421fe0b1973f52a9dbfcf3ea88bff1
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="heapmin"></a>_heapmin
Libera la memoria del montón no utilizada al sistema operativo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _heapmin( void );  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, `_heapmin` devuelve 0; en caso contrario, la función devuelve -1 y establece `errno` en `ENOSYS`.  
  
 Para obtener más información sobre este y otros códigos de retorno, consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Comentarios  
 La función `_heapmin` minimiza el montón al liberar memoria del montón no utilizada al sistema operativo. Si el sistema operativo no admite `_heapmin`(por ejemplo, Windows 98), la función devuelve -1 y establece `errno` a `ENOSYS`.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|-------------|---------------------|---------------------|  
|`_heapmin`|\<malloc.h>|\<errno.h>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="see-also"></a>Vea también  
 [Asignación de memoria](../../c-runtime-library/memory-allocation.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [_heapadd](../../c-runtime-library/heapadd.md)   
 [_heapchk](../../c-runtime-library/reference/heapchk.md)   
 [_heapset](../../c-runtime-library/heapset.md)   
 [_heapwalk](../../c-runtime-library/reference/heapwalk.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)