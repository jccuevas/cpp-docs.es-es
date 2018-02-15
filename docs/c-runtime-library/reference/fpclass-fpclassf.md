---
title: _fpclass, _fpclassf | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _fpclass
- _fpclassf
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
- fpclass
- _fpclass
- _fpclassf
- math/_fpclass
- float/_fpclass
- math/_fpclassf
dev_langs:
- C++
helpviewer_keywords:
- fpclass function
- floating-point numbers, IEEE representation
- _fpclass function
- _fpclassf function
ms.assetid: 2774872d-3543-446f-bc72-db85f8b95a6b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a13abc84cf3e28f6282bf5c160d118d019334cfd
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="fpclass-fpclassf"></a>_fpclass, _fpclassf
Devuelve un valor que indica la clasificación de punto flotante del argumento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _fpclass(   
   double x   
);  
  
int _fpclassf(   
   float x   
); /* x64 only */  
```  
  
#### <a name="parameters"></a>Parámetros  
 `x`  
 Valor de punto flotante que se va a probar.  
  
## <a name="return-value"></a>Valor devuelto  
 Las funciones `_fpclass` y `_fpclassf` devuelven un valor entero que indica la clasificación de punto flotante del argumento `x`. Es posible que la clasificación tenga uno de los valores siguientes, que se definen en \<float.h>.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`_FPCLASS_SNAN`|NaN de señalización|  
|`_FPCLASS_QNAN`|NaN reservado|  
|`_FPCLASS_NINF`|Infinito negativo (-INF)|  
|`_FPCLASS_NN`|Negativo normalizado distinto de cero|  
|`_FPCLASS_ND`|Negativo no normalizado|  
|`_FPCLASS_NZ`|Cero negativo (- 0)|  
|`_FPCLASS_PZ`|Cero positivo (+0)|  
|`_FPCLASS_PD`|Positivo no normalizado|  
|`_FPCLASS_PN`|Positivo normalizado distinto de cero|  
|`_FPCLASS_PINF`|Infinito positivo (+INF)|  
  
## <a name="remarks"></a>Comentarios  
 Las funciones `_fpclass` y `_fpclassf` son específicas de Microsoft. Son similares a [fpclassify](../../c-runtime-library/reference/fpclassify.md), pero devuelven información más detallada sobre el argumento. La función `_fpclassf` solo está disponible cuando se compila para la plataforma x64.  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario|  
|--------------|---------------------|  
|`_fpclass`|\<float.h>|  
  
 Para obtener más información sobre compatibilidad y conformidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [isnan, _isnan, _isnanf](../../c-runtime-library/reference/isnan-isnan-isnanf.md)   
 [fpclassify](../../c-runtime-library/reference/fpclassify.md)