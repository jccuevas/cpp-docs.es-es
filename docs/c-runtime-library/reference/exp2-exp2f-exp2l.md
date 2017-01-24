---
title: "Exp2, exp2f, exp2l | Microsoft Docs"
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
  - "exp2"
  - "exp2f"
  - "exp2l"
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
  - "exp2"
  - "math/exp2"
  - "exp2f"
  - "math/exp2f"
  - "exp2l"
  - "math/exp2l"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "exp2 (función)"
  - "exp2f (función)"
  - "exp2l (función)"
ms.assetid: 526e3e10-201a-4610-a886-533f44ece344
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Exp2, exp2f, exp2l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Calcula 2 provoca que el valor especificado \(es decir, 2ˣ\).  
  
## Sintaxis  
  
```  
double exp2(  
   double x  
);  
  
float exp2(  
   float x  
);  // C++ only  
  
long double exp2(  
   long double x  
); // C++ only  
  
float exp2f(  
   float x  
);  
  
long double exp2l(  
   long double x  
);  
  
```  
  
#### Parámetros  
 \[in\] `x`  
 El valor del exponente.  
  
## Valor devuelto  
 Si se realiza correctamente, devuelve el exponente de base 2 de `x` \(2ˣ\). De lo contrario, puede devolver uno de los siguientes valores:  
  
|Problema|Volver|  
|--------------|------------|  
|`x` \= ±0|1|  
|`x` \= \- INFINITO|\+0|  
|`x` \= \+ INFINITO|\+ INFINITO|  
|`x` \= NaN|NaN|  
|Error de desbordamiento de intervalo|\+ HUGE\_VAL \+ HUGE\_VALF, o \+ HUGE\_VALL|  
|Error de intervalo de subdesbordamiento|resultado correcto, después de redondearlo|  
  
 Los errores se notifican como se especifica en [\_matherr](../../c-runtime-library/reference/matherr.md).  
  
## Comentarios  
 Como C\+\+ permite las sobrecargas, puede llamar a las sobrecargas de `exp2` que toman y devuelven los tipos float y double de tiempo. En un programa de C, `exp2` siempre toma y devuelve un tipo double.  
  
## Requisitos  
  
|Rutina|Encabezado C|Encabezado C\+\+|  
|------------|------------------|----------------------|  
|`exp`, `expf`, `expl`|\<math.h\>|\<cmath\>|  
  
 Para obtener información adicional sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [exp, expf](../../c-runtime-library/reference/exp-expf.md)   
 [LOG2, log2f, log2l](../../c-runtime-library/reference/log2-log2f-log2l.md)