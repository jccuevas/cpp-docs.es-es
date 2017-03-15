---
title: "FMA, fmaf, fmal | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fma"
  - "fmaf"
  - "fmal"
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
  - "fma"
  - "fmaf"
  - "fmal"
  - "math/fma"
  - "math/fmaf"
  - "math/fmal"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fma (función)"
  - "fmaf (función)"
  - "fmal (función)"
ms.assetid: 584a6037-da1e-4e86-9f0c-97aae86de0c0
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# FMA, fmaf, fmal
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Multiplica dos valores juntos, agrega un tercer valor y, a continuación, se redondea el resultado, sin perder cualquier precisión debida al redondeo intermediario.  
  
## Sintaxis  
  
```  
double fma(  
   double x,   
   double y,   
   double z  
);  
  
float fma(  
   float  x,   
   float  y,   
   float z  
); //C++ only  
  
long double fma(  
   long double  x,   
   long double  y,   
   long double z  
); //C++ only  
  
float fmaf(  
   float  x,   
   float  y,   
   float z  
);  
  
long double fmal(  
   long double  x,   
   long double  y,   
   long double z  
);  
  
```  
  
#### Parámetros  
 \[in\] `x`  
 Primer valor que se va a multiplicar.  
  
 \[in\] `y`  
 Segundo valor que se va a multiplicar.  
  
 \[in\] `z`  
 El valor que se va a agregar.  
  
## Valor devuelto  
 Returns \(`x` ×    `y`\) \+ `z`. El valor devuelto, a continuación, se redondea utilizando el formato de redondeo actual.  
  
 De lo contrario, puede devolver uno de los siguientes valores:  
  
|Problema|Volver|  
|--------------|------------|  
|`x` \= INFINITO, `y` \= 0 o<br /><br /> `x` \= 0, `y` \= INFINITO|NaN|  
|`x` o `y` \= ± exacta infinito, `z` \= infinito con el signo opuesto|NaN|  
|`x` o `y` \= NaN|NaN|  
|no \(`x` \= 0, `y`\= indefinido\) y `z` \= NaN<br /><br /> no \(`x`\= indefinida, `y`\= 0\) y `z` \= NaN|NaN|  
|Error de desbordamiento de intervalo|±HUGE\_VAL, ±HUGE\_VALF o ±HUGE\_VALL|  
|Error de intervalo de subdesbordamiento|valor correcto después de redondearlo.|  
  
 Los errores se notifican como se especifica en [\_matherr](../../c-runtime-library/reference/matherr.md).  
  
## Comentarios  
 Como C\+\+ permite las sobrecargas, puede llamar a las sobrecargas de `fma` que toman y devuelven los tipos float y double de tiempo. En un programa de C, `fma` siempre toma y devuelve un tipo double.  
  
 Esta función calcula el valor como si se realizaron con precisión infinita y, a continuación, se redondea el resultado final.  
  
## Requisitos  
  
|Función|Encabezado C|Encabezado C\+\+|  
|-------------|------------------|----------------------|  
|`fma`, `fmaf`,  `fmal`|\<math.h\>|\<cmath\>|  
  
 Para obtener información adicional sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [remainder, remainderf, remainderl](../../c-runtime-library/reference/remainder-remainderf-remainderl.md)   
 [remquo, remquof, remquol](../../c-runtime-library/reference/remquo-remquof-remquol.md)