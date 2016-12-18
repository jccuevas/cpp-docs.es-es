---
title: "lgamma, lgammaf, lgammal | Microsoft Docs"
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
  - "lgamma"
  - "lgammaf"
  - "lgammal"
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
  - "lgamma"
  - "lgammaf"
  - "lgammal"
  - "math/lgamma"
  - "math/lgammaf"
  - "math/lgammal"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "lgamma (función)"
  - "lgammal (función)"
  - "lgammaf (función)"
ms.assetid: 6e326c58-7077-481a-a329-c82ae56ae9e6
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# lgamma, lgammaf, lgammal
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Determina el logaritmo natural del valor absoluto de la función gamma del valor especificado.  
  
## Sintaxis  
  
```  
double lgamma(  
   double x  
);  
  
float lgamma(  
   float x  
); //C++ only  
  
long double lgamma(  
   long double x  
); //C++ only  
  
float lgammaf(  
   float x  
);  
  
long double lgammal(  
   long double x  
);  
  
```  
  
#### Parámetros  
 \[in\] `x`  
 El valor para calcular.  
  
## Valor devuelto  
 Si se realiza correctamente, devuelve el logaritmo natural del valor absoluto de la función gamma de `x.`  
  
|Problema|Volver|  
|--------------|------------|  
|`x` \= NaN|NaN|  
|`x` \= ±0|\+ INFINITO|  
|`x`\= entero negativo|\+ INFINITO|  
|±INFINITY|\+ INFINITO|  
|error de polo|\+ HUGE\_VAL \+ HUGE\_VALF, o \+ HUGE\_VALL|  
|error de desbordamiento de intervalo|±HUGE\_VAL, ±HUGE\_VALF o ±HUGE\_VALL|  
  
 Los errores se notifican como se especifica en [\_matherr](../../c-runtime-library/reference/matherr.md).  
  
## Comentarios  
 Como C\+\+ permite las sobrecargas, puede llamar a las sobrecargas de `lgamma` que toman y devuelven los tipos float y double de tiempo. En un programa de C, `lgamma` siempre toma y devuelve un tipo double.  
  
 Si x es un número racional, esta función devuelve el logaritmo de factorial \(`x`\-1\).  
  
## Requisitos  
  
|Función|Encabezado C|Encabezado C\+\+|  
|-------------|------------------|----------------------|  
|`lgamma`, `lgammaf`,  `lgammal`|\<math.h\>|\<cmath\>|  
  
 Para obtener información adicional sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [tgamma, tgammaf, tgammal](../../c-runtime-library/reference/tgamma-tgammaf-tgammal.md)