---
title: _set_doserrno | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _set_doserrno
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _set_doserrno
- set_doserrno
dev_langs: C++
helpviewer_keywords:
- _set_doserrno function
- doserrno global variable
- set_doserrno function
- _doserrno global variable
ms.assetid: 8686c159-3797-4705-a53e-7457869ca6f3
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 63824d9a9bd9e05d184656f641dca52891c7f0cd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="setdoserrno"></a>_set_doserrno
Establece el valor de la variable global [_doserrno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
errno_t _set_doserrno(   
   int value   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `value`  
 Valor nuevo de `_doserrno`.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve cero si es correcto.  
  
## <a name="remarks"></a>Comentarios  
 Los valores posibles se definen en Errno.h.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|-------------|---------------------|---------------------|  
|`_set_doserrno`|\<stdlib.h>|\<errno.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="see-also"></a>Vea también  
 [_get_doserrno](../../c-runtime-library/reference/get-doserrno.md)   
 [errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)