---
title: "erf, erff, erfl, erfc, erfcf, erfcl | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "erff"
  - "erfl"
  - "erf"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-math-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "erfl"
  - "erf"
  - "erff"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "erf (función)"
  - "erff (función)"
  - "erfl (función)"
ms.assetid: 144d90d3-e437-41c2-a659-cd57596023b5
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# erf, erff, erfl, erfc, erfcf, erfcl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Calcula la función de error o la función de error complementaria de un valor.  
  
## Sintaxis  
  
```  
double erf(    double x ); float erf(    float x ); // C++ only long double erf(    long double x ); // C++ only float erff(    float x ); long double erfl(    long double x ); double erfc(    double x ); float erfc(    float x ); // C++ only long double erfc(    long double x ); // C++ only float erfcf(    float x ); long double erfcl(    long double x );  
```  
  
#### Parámetros  
 `x`  
 Valor de punto flotante.  
  
## Valor devuelto  
 Las funciones `erf` devuelven la función de error de Gauss `x`.  Las funciones `erfc` devuelven la función de error de Gauss complementaria `x`.  
  
## Comentarios  
 Las funciones `erf` calculan la función de error de Gauss x, que se define así:  
  
 ![Función de error de x](../../c-runtime-library/reference/media/crt_erf_formula.png "CRT\_erf\_formula")  
  
 La función de error de Gauss complementaria se define como 1 – erf\(x\).  Las funciones `erf` devuelven un valor dentro del intervalo comprendido entre \-1,0 y 1,0.  No se devuelve ningún error.  Las funciones `erfc` devuelven un valor dentro del intervalo comprendido entre 0 y 2.  Si `x` es demasiado grande para `erfc`, la variable `errno` se establece en `ERANGE`.  
  
 Como C\+\+ permite las sobrecargas, puede llamar a las sobrecargas de `erf` y `erfc`, que toman y devuelven los tipos `float` y `long double`.  En un programa de C, `erf` y `erfc` siempre toman y devuelven `double`.  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`erf`, `erff`, `erfl`, `erfc`, `erfcf`, `erfcl`|\<math.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)