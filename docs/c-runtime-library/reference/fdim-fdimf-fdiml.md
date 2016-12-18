---
title: "fdim, fdimf, fdiml | Microsoft Docs"
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
  - "fdim"
  - "fdimf"
  - "fdiml"
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
  - "fdim"
  - "fdimf"
  - "fdiml"
  - "math/fdim"
  - "math/fdimf"
  - "math/fdiml"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "fdim (función)"
  - "fdimf (función)"
  - "fdiml (función)"
ms.assetid: 2d4ac639-51e9-462d-84ab-fb03b06971a0
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fdim, fdimf, fdiml
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Determina la diferencia entre el primer y segundo valor positiva.  
  
## Sintaxis  
  
```  
double fdim(  
   double x,   
   double y  
);  
  
float fdim(  
   float x,   
   float y  
); //C++ only  
  
long double fdim(  
   long double x,   
   long double y  
); //C++ only  
  
float fdimf(  
   float x,   
   float y  
);  
  
long double fdiml(  
   long double x,   
   long double y  
);  
  
```  
  
#### Parámetros  
 \[in\] `x`  
 Primer valor.  
  
 \[in\] `y`  
 Segundo valor.  
  
## Valor devuelto  
 Devuelve la diferencia positiva entre `x` y `y`:  
  
|Valor devuelto|Escenario|  
|--------------------|---------------|  
|x e y|Si x \> y|  
|0|Si x \< \= s|  
  
 De lo contrario, puede devolver uno de los siguientes errores:  
  
|Problema|Volver|  
|--------------|------------|  
|Error de desbordamiento de intervalo|\+ HUGE\_VAL \+ HUGE\_VALF, o \+ HUGE\_VALL|  
|Error de intervalo de subdesbordamiento|valor correcto \(después de redondearlo\)|  
|`x` o `y` es NaN|NaN|  
  
 Los errores se notifican como se especifica en [\_matherr](../../c-runtime-library/reference/matherr.md).  
  
## Comentarios  
 Como C\+\+ permite las sobrecargas, puede llamar a las sobrecargas de `fdim` que toman y devuelven los tipos float y double de tiempo. En un programa de C, `fdim` siempre toma y devuelve un tipo double.  
  
 Excepto para el control de NaN, esta función es equivalente a [Fmax, fmaxf, fmaxl](../../c-runtime-library/reference/fmax-fmaxf-fmaxl.md)\(`x`\-`y,` 0\).  
  
## Requisitos  
  
|Función|Encabezado C|Encabezado C\+\+|  
|-------------|------------------|----------------------|  
|`fdim`, `fdimf`,  `fdiml`|\<math.h\>|\<cmath\>|  
  
 Para obtener información adicional sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [Fmax, fmaxf, fmaxl](../../c-runtime-library/reference/fmax-fmaxf-fmaxl.md)   
 [ABS, laboratorios, llabs, \_abs64](../../c-runtime-library/reference/abs-labs-llabs-abs64.md)