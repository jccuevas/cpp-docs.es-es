---
title: "Fmax, fmaxf, fmaxl | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fmax"
  - "fmaxf"
  - "fmaxl"
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
  - "fmax"
  - "fmaxf"
  - "fmaxl"
  - "math/fmax"
  - "math/fmaxf"
  - "math/fmaxl"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "fmax (función)"
  - "fmaxf (función)"
  - "fmaxl (función)"
ms.assetid: a773ccf7-495e-4a9a-8c6d-dfb53e341e35
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Fmax, fmaxf, fmaxl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Determinar el mayor de dos valores numéricos especificados.  
  
## Sintaxis  
  
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
  
#### Parámetros  
 \[in\] `x`  
 Primer valor que se va a comparar.  
  
 \[in\] `y`  
 Segundo valor que se va a comparar.  
  
## Valor devuelto  
 Si se realiza correctamente, devuelve el mayor de `x` o `y`. El valor devuelto es exacto y no depende de ninguna forma de redondeo.  
  
 De lo contrario, puede devolver uno de los siguientes valores:  
  
|Problema|Volver|  
|--------------|------------|  
|`x` \= NaN|`y`|  
|`y` \= NaN|`x`|  
|`x` y `y` \= NaN|NaN|  
  
 Esta función no utiliza los errores especificados en  [\_matherr](../../c-runtime-library/reference/matherr.md).  
  
## Comentarios  
 Como C\+\+ permite las sobrecargas, puede llamar a sobrecargas de fmax que toman y devuelven los tipos float y double de tiempo. En un programa de C, fmax siempre toma y devuelve un valor double.  
  
## Requisitos  
  
|Función|Encabezado C|Encabezado C\+\+|  
|-------------|------------------|----------------------|  
|`fmax`, `fmaxf`, `fmaxl`|\<math.h\>|\<cmath\>|  
  
 Para obtener información adicional sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fmin, fminf, fminl](../Topic/fmin,%20fminf,%20fminl1.md)