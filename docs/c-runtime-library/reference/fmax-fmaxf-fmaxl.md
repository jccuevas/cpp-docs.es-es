---
title: fmax, fmaxf, fmaxl | Microsoft Docs
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
- fmax
- fmaxf
- fmaxl
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
- fmax
- fmaxf
- fmaxl
- math/fmax
- math/fmaxf
- math/fmaxl
dev_langs: C++
helpviewer_keywords:
- fmax function
- fmaxf function
- fmaxl function
ms.assetid: a773ccf7-495e-4a9a-8c6d-dfb53e341e35
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6f580738ba73a7e0a8fac8662be7126edb5a9e95
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="fmax-fmaxf-fmaxl"></a>fmax, fmaxf, fmaxl
Determina el mayor de dos valores numéricos especificados.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
double fmax(  
   double x,   
   double y  
);  
  
float fmax(  
   float x,   
   float y  
); //C++ only  
  
long double fmax(  
   long double x,   
   long double y  
); //C++ only  
  
float fmaxf(  
   float x,   
   float y  
);  
  
long double fmaxl(  
   long double x,   
   long double y  
);  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `x`  
 Primer valor que se va a comparar.  
  
 [in] `y`  
 Segundo valor que se va a comparar.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve el valor mayor de `x` o `y`. El valor devuelto es exacto y no depende de ninguna forma de redondeo.  
  
 De lo contrario, es posible que devuelva uno de los siguientes valores:  
  
|Problema|Volver|  
|-----------|------------|  
|`x` = NaN|`y`|  
|`y` = NaN|`x`|  
|`x` y `y` = NaN|NaN|  
  
 Esta función no usa los errores especificados en [_matherr](../../c-runtime-library/reference/matherr.md).  
  
## <a name="remarks"></a>Comentarios  
 Dado que C++ admite sobrecargas, puede llamar a las sobrecargas de fmax que toman y devuelven los tipos float y long double. En un programa de C, fmax siempre toma y devuelve un tipo double.  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado C|Encabezado C++|  
|--------------|--------------|------------------|  
|`fmax`, `fmaxf`, `fmaxl`|\<math.h>|\<cmath> o \<math.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fmin, fminf, fminl](fmin-fminf-fminl.md)  