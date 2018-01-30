---
title: nearbyint, nearbyintf, nearbyintl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- nearbyint
- nearbyintf
- nerabyintl
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
- nearbyint
- nearbyintf
- nearbyintl
- math/nearbyint
- math/narbyintf
- math/narbyintl
dev_langs:
- C++
helpviewer_keywords:
- nearbyint function
- nearbyintf function
- nearbyintl function
ms.assetid: dd39cb68-96b0-434b-820f-6ff2ea65584f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0d981df622450ef0b52a9b0d81427497a3e180bc
ms.sourcegitcommit: 185e11ab93af56ffc650fe42fb5ccdf1683e3847
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2018
---
# <a name="nearbyint-nearbyintf-nearbyintl"></a>nearbyint, nearbyintf, nearbyintl
Redondea el valor de punto flotante especificado en un entero y devuelve ese valor con un formato de punto flotante.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
double nearbyint(  
   double x  
);  
  
float nearbyint(  
   float x  
); //C++ only  
  
long double nearbyint(  
   long double x  
); //C++ only  
  
float nearbyintf(  
   float x  
);  
  
long double nearbyintl(  
   long double x  
);  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `x`  
 El valor que se va a redondear.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `x`, redondeado al entero más cercano usando el formato de redondeo actual, de acuerdo con lo que se defina en fegetround. De lo contrario, es posible que la función devuelva uno de los siguientes valores:  
  
|Problema|Volver|  
|-----------|------------|  
|`x`= ±INFINITY|±Infinity, sin cambios|  
|`x` = ±0|± 0, sin cambios|  
|`x` = NaN|NaN|  
  
 Los errores no se notifican a través de [_matherr](../../c-runtime-library/reference/matherr.md); en concreto, esta función no notifica ninguna excepción FE_INEXACT.  
  
## <a name="remarks"></a>Comentarios  
 La principal diferencia entre esta función y `rint` es que esta función no genera la excepción de punto flotante inexacta.  
  
 Dado que los valores de punto flotante máximos son enteros exactos, esta función nunca se desbordará por sí misma, sino que la salida podría desbordar el valor devuelto, según la versión de la función que use.  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado C|Encabezado C++|  
|--------------|--------------|------------------|  
|`nearbyint`,                `nearbyintf`,  `nearbyintl`|\<math.h>|\<cmath>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)