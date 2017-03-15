---
title: "LOG2, log2f, log2l | Microsoft Docs"
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
  - "log2"
  - "log2l"
  - "log2f"
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
dev_langs: 
  - "C++"
ms.assetid: 94d11b38-70b7-4d3a-94ac-523153c92b2e
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# LOG2, log2f, log2l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Determina el binario logaritmo \(base 2\) del valor especificado.  
  
## Sintaxis  
  
```  
double log2(  
   double x  
);  
  
float log2(  
   float x  
); //C++ only  
  
long double log2(  
   long double x  
); //C++ only  
  
float log2f(  
   float x  
);  
  
long double log2l(  
   long double x  
);  
  
```  
  
#### Parámetros  
 \[in\] `x`  
 El valor para determinar el logaritmo en base 2 de.  
  
## Valor devuelto  
 Si se ejecuta correctamente, devuelve el retorno log2 `x`.  
  
 De lo contrario, puede devolver uno de los siguientes valores:  
  
|Problema|Volver|  
|--------------|------------|  
|`x` \< 0|NaN|  
|`x` \= ±0|\-INFINITO|  
|`x` \= 1|\+0|  
|\+ INFINITO|\+ INFINITO|  
|NaN|NaN|  
|error de dominio|NaN|  
|error de polo|\-HUGE\_VAL, \- HUGE\_VALF, o \- HUGE\_VALL|  
  
 Los errores se notifican como se especifica en [\_matherr](../../c-runtime-library/reference/matherr.md).  
  
## Comentarios  
 Si x es un entero, esta función devuelve esencialmente el índice de base cero del bit más significativo 1 de `x`.  
  
## Requisitos  
  
|Función|Encabezado C|Encabezado C\+\+|  
|-------------|------------------|----------------------|  
|`log2`, `log2f`,  `log2l`|\<math.h\>|\<cmath\>|  
  
 Para obtener información adicional sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [Exp2, exp2f, exp2l](../../c-runtime-library/reference/exp2-exp2f-exp2l.md)   
 [log, logf, log10, log10f](../../c-runtime-library/reference/log-logf-log10-log10f.md)