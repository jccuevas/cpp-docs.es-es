---
title: _finite, _finitef | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _finite
- _finitef
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
- finite
- _finite
- _finitef
- math/_finite
- math/_finitef
- float/_finite
dev_langs: C++
helpviewer_keywords:
- finite function
- _finite function
- _finitef function
ms.assetid: 5a7d7ca7-befb-4e1f-831d-28713c6eb805
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cb08c6a525222e8c1bb886f87aa55b2996cd3846
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="finite-finitef"></a>_finite, _finitef
Determina si un valor de punto flotante es finito.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _finite(   
   double x   
);  
  
int _finitef(   
   float x   
); /* x64 and ARM/ARM64 only */  
```  
  
#### <a name="parameters"></a>Parámetros  
 `x`  
 Valor de punto flotante que se va a probar.  
  
## <a name="return-value"></a>Valor devuelto  
 Ambos `_finite` y `_finitef` devuelven un valor distinto de cero si el argumento *x* es finito; es decir, si -INF < `x` < + INF. Devuelve 0 si el argumento es infinito o un valor NaN (no es un número).  
  
## <a name="remarks"></a>Comentarios  
 Las funciones `_finite` y `_finitef` son específicas de Microsoft. La función `_finitef` solo está disponible cuando se compila para las plataformas x86, ARM o ARM64.  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario (C)|Encabezado necesario (C++)|  
|--------------|---------------------------|-------------------------------|  
|`_finite`|\<float.h> o \<math.h>|\<float.h>, \<math.h>, \<cfloat> o \<cmath>|  
|`_finitef`|\<math.h>|\<math.h> o \<cmath>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [isnan, _isnan, _isnanf](../../c-runtime-library/reference/isnan-isnan-isnanf.md)   
 [_fpclass, _fpclassf](../../c-runtime-library/reference/fpclass-fpclassf.md)