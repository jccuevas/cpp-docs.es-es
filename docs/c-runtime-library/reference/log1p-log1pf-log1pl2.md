---
title: "log1p, log1pf, log1pl2 | Microsoft Docs"
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
  - "log1p"
  - "log1pf"
  - "log1pl"
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
  - "log1p"
  - "log1pf"
  - "log1pl"
  - "math/log1p"
  - "math/log1pf"
  - "math/log1pl"
helpviewer_keywords: 
  - "log1p (función)"
  - "log1pf (función)"
  - "log1pl (función)"
ms.assetid: a40d965d-b4f6-42f4-ba27-2395546f7c12
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# log1p, log1pf, log1pl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Calcula el logaritmo natural de 1 más el valor especificado.  
  
## Sintaxis  
  
```  
double log1p(  
   double x  
);  
  
float log1p(  
   float x  
); //C++ only  
  
long double log1p(  
   long double x  
); //C++ only  
  
float log1pf(  
   float x  
);  
  
long double log1pl(  
   long double x  
);  
  
```  
  
#### Parámetros  
 `x`  
 El argumento de punto flotante.  
  
## Valor devuelto  
 Si se realiza correctamente, devuelve el logaritmo natural \(base e\) de \(`x`\+ 1\).  
  
 De lo contrario, puede devolver uno de los siguientes valores:  
  
|Entrada|Resultado|Excepción SEH|errno|  
|-------------|---------------|-------------------|-----------|  
|\+ inf|\+ inf|||  
|Desnormalizados|Igual que la entrada|SUBDESBORDAMIENTO||  
|±0|Igual que la entrada|||  
|\-1|\-inf|DIVBYZERO|ERANGE|  
|\< \-1|NaN|INVALID|EDOM|  
|\-inf|NaN|INVALID|EDOM|  
|±SNaN|Igual que la entrada|INVALID||  
|±QNaN, indefinido|Igual que la entrada|||  
  
 El `errno` el valor ERANGE si `x` \= \-1. El `errno` el valor EDOM si `x` \< −1.  
  
## Comentarios  
 El `log1p` funciones pueden ser más precisas que el uso de registro \(`x`\+ 1\) cuando x es cercanos a 0.  
  
 Como C\+\+ permite las sobrecargas, puede llamar a las sobrecargas de `log1p` que toman y devuelven los tipos float y double de tiempo. En un programa de C, `log1p` siempre toma y devuelve un tipo double.  
  
 Si `x` es un número natural, esta función devuelve el logaritmo de factorial \(`x`\-1\).  
  
## Requisitos  
  
|Función|Encabezado C|Encabezado C\+\+|  
|-------------|------------------|----------------------|  
|`log1p`, `log1pf`,  `log1pl`|\<math.h\>|\<cmath\>|  
  
 Para obtener información adicional sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [LOG2, log2f, log2l](../../c-runtime-library/reference/log2-log2f-log2l.md)   
 [log, logf, log10, log10f](../../c-runtime-library/reference/log-logf-log10-log10f.md)