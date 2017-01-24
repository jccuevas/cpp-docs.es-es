---
title: "tgamma, tgammaf, tgammal | Microsoft Docs"
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
  - "tgamma"
  - "tgammaf"
  - "tgammal"
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
  - "tgamma"
  - "tgammaf"
  - "tgammal"
  - "math/tgamma"
  - "math/tgammaf"
  - "math/tgammal"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "tgamma (función)"
  - "tgammaf (función)"
  - "tgammal (función)"
ms.assetid: f1bd2681-8af2-48a9-919d-5358fd068acd
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# tgamma, tgammaf, tgammal
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Determina la función gamma del valor especificado.  
  
## Sintaxis  
  
```  
double tgamma(  
   double x  
);  
  
float tgamma(  
   float x  
); //C++ only  
  
long double tgamma(  
   long double x  
); //C++ only  
  
float tgammaf(  
   float x  
);  
  
long double tgammal(  
   long double x  
);  
  
```  
  
#### Parámetros  
 \[in\] `x`  
 El valor para buscar el valor gamma de.  
  
## Valor devuelto  
 Si se realiza correctamente, devuelve el valor gamma de `x`.  
  
 Puede producirse un error de intervalo si la magnitud de `x` es demasiado grande o demasiado pequeño para el tipo de datos. Puede producirse un error de dominio o intervalo si `x` \< \= 0.  
  
|Problema|Volver|  
|--------------|------------|  
|x \= ± 0|±INFINITY|  
|x \= entero negativo|NaN|  
|x \= \- infinito|NaN|  
|x \= \+ infinito|\+ INFINITO|  
|x \= NaN|NaN|  
|error de dominio|NaN|  
|error de polo|±HUGE\_VAL, ±HUGE\_VALF o ±HUGE\_VALL|  
|error de desbordamiento de intervalo|±HUGE\_VAL, ±HUGE\_VALF o ±HUGE\_VALL|  
|error de intervalo de subdesbordamiento|el valor correcto después de redondearlo.|  
  
 Los errores se notifican como se especifica en [\_matherr](../../c-runtime-library/reference/matherr.md).  
  
## Comentarios  
 Como C\+\+ permite las sobrecargas, puede llamar a sobrecargas de tgamma que toman y devuelven los tipos float y double de tiempo. En un programa de C, tgamma siempre toma y devuelve un valor double.  
  
 Si x es un número natural, esta función devuelve el factorial de \(x\-1\).  
  
## Requisitos  
  
|Función|Encabezado C|Encabezado C\+\+|  
|-------------|------------------|----------------------|  
|`tgamma`, `tgammaf`,  `tgammal`|\<math.h\>|\<cmath\>|  
  
 Para obtener información adicional sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [lgamma, lgammaf, lgammal](../../c-runtime-library/reference/lgamma-lgammaf-lgammal.md)