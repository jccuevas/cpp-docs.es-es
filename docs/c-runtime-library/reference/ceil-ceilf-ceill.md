---
title: ceil, ceilf, ceill | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- ceilf
- ceil
- ceill
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
- ceil
- ceilf
- ceill
dev_langs:
- C++
helpviewer_keywords:
- calculating value ceilings
- ceill function
- ceil function
- ceilf function
ms.assetid: f4e5acab-5c8f-4b10-9ae2-9561e6453718
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 1fd4b888c8fc332c07aed62af03b340864dfe3bf
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="ceil-ceilf-ceill"></a>ceil, ceilf, ceill
Calcula el límite superior de un valor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
double ceil(   
   double x   
);  
float ceil(  
   float x  
);  // C++ only  
long double ceil(  
   long double x  
);  // C++ only  
float ceilf(  
   float x  
);  
long double ceill(  
   long double x  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `x`  
 Valor de punto flotante.  
  
## <a name="return-value"></a>Valor devuelto  
 Las funciones `ceil` devuelven un valor de punto flotante que representa el entero más pequeño que sea mayor o igual que `x`. No se devuelve ningún error.  
  
|Entrada|Excepción SEH|Excepción de Matherr|  
|-----------|-------------------|-----------------------|  
|± `QNAN`,`IND`|ninguna|`_DOMAIN`|  
  
 `ceil` tiene una implementación que usa las Extensiones SIMD de transmisión por secuencias 2 (SSE2). Para obtener información y conocer las restricciones sobre el uso de la implementación de SSE2, consulte [_set_SSE2_enable](../../c-runtime-library/reference/set-sse2-enable.md).  
  
## <a name="remarks"></a>Comentarios  
 Dado que C++ admite sobrecargas, puede llamar a sobrecargas de `ceil`. En un programa de C, `ceil` siempre toma y devuelve un tipo double.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`ceil`, `ceilf`, `ceill`|\<math.h>|  
  
 Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
 Consulte el ejemplo de [floor](../../c-runtime-library/reference/floor-floorf-floorl.md).  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [floor, floorf, floorl](../../c-runtime-library/reference/floor-floorf-floorl.md)   
 [fmod, fmodf](../../c-runtime-library/reference/fmod-fmodf.md)   
 [round, roundf, roundl](../../c-runtime-library/reference/round-roundf-roundl.md)
