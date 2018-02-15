---
title: erf, erff, erfl, erfc, erfcf, erfcl | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- erff
- erfl
- erf
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
- erfl
- erf
- erff
dev_langs:
- C++
helpviewer_keywords:
- erfl function
- erff function
- erf function
ms.assetid: 144d90d3-e437-41c2-a659-cd57596023b5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fa60c6bb6c3c11a596589a411a7d094cc41c65fa
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="erf-erff-erfl-erfc-erfcf-erfcl"></a>erf, erff, erfl, erfc, erfcf, erfcl
Calcula la función de error o la función de error complementaria de un valor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
double erf(  
   double x  
);  
float erf(  
   float x  
); // C++ only  
long double erf(  
   long double x  
); // C++ only  
float erff(  
   float x  
);  
long double erfl(  
   long double x  
);  
double erfc(  
   double x  
);  
float erfc(  
   float x  
); // C++ only  
long double erfc(  
   long double x  
); // C++ only  
float erfcf(  
   float x  
);  
long double erfcl(  
   long double x  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `x`  
 Valor de punto flotante.  
  
## <a name="return-value"></a>Valor devuelto  
 Las funciones `erf` devuelven la función de error de Gauss `x`. Las funciones `erfc` devuelven la función de error de Gauss complementaria `x`.  
  
## <a name="remarks"></a>Comentarios  
 Las funciones `erf` calculan la función de error de Gauss x, que se define así:  
  
 ![Función de error de x](../../c-runtime-library/reference/media/crt_erf_formula.PNG "CRT_erf_formula")  
  
 La función error de Gauss complementaria se define como 1 - ERF. Las funciones `erf` devuelven un valor dentro del intervalo comprendido entre -1,0 y 1,0. No se devuelve ningún error. Las funciones `erfc` devuelven un valor dentro del intervalo comprendido entre 0 y 2. Si `x` es demasiado grande para `erfc`, la variable `errno` se establece en `ERANGE`.  
  
 Como C++ permite las sobrecargas, puede llamar a las sobrecargas de `erf` y `erfc`, que toman y devuelven los tipos `float` y `long double`. En un programa de C, `erf` y `erfc` siempre toman y devuelven `double`.  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario|  
|--------------|---------------------|  
|`erf`, `erff`, `erfl`, `erfc`, `erfcf`, `erfcl`|\<math.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)