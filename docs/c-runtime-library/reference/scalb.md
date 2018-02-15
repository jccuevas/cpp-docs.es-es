---
title: _scalb | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _scalb
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- scalb
- _scalb
dev_langs:
- C++
helpviewer_keywords:
- exponential calculations
- _scalb function
- scalb function
ms.assetid: 148cf5a8-b405-44bf-a1f0-7487adba2421
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3f68d1e14a4f92c2ed7ee481966dc46c4384341f
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="scalb"></a>_scalb
Escala el argumento por una potencia de 2.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
double _scalb(  
   double x,  
   long exp   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `x`  
 Valor de punto flotante de precisión doble.  
  
 `exp`  
 Exponente de entero largo.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un valor exponencial si es correcto. Si se produce desbordamiento (según cuál sea el signo de `x`), `_scalb` devuelve `HUGE_VAL`; el `errno` variable se establece en `ERANGE`.  
  
 Para obtener más información sobre este y otros códigos de retorno, consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Comentarios  
 La función `_scalb` calcula el valor de `x *` 2exp.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_scalb`|\<float.h>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [ldexp](../../c-runtime-library/reference/ldexp.md)