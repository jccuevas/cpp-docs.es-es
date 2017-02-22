---
title: "expm1, expm1f, expm1l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "expm1l"
  - "expm1"
  - "expm1f"
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
  - "expm1l"
  - "expm1"
  - "expm1f"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "expm1 (función)"
  - "expm1f (función)"
  - "expm1l (función)"
ms.assetid: 2a4dd2d9-370c-42b0-9067-0625efa272e0
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# expm1, expm1f, expm1l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Calcula el exponencial de base e de un valor menos uno.  
  
## Sintaxis  
  
```  
double expm1(   
   double x   
);  
float expm1(  
   float x  
);  // C++ only  
long double expm1(  
   long double x  
);  // C++ only  
float expm1f(  
   float x  
);  
long double expm1l(  
   long double x  
);  
```  
  
#### Parámetros  
 `x`  
 El valor exponencial de punto flotante.  
  
## Valor devuelto  
 Las funciones `expm1` devuelven un valor de punto flotante que representa e<sup>x</sup> – 1, si se realizan correctamente.  Cuando se produce desbordamiento, `expm1` devuelve `HUGE_VAL`, `expm1f` devuelve `HUGE_VALF`, `expm1l` devuelve `HUGE_VALL` y `errno` se establece en `ERANGE`.  Para obtener más información sobre los códigos de retorno, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 Como C\+\+ permite las sobrecargas, puede llamar a las sobrecargas de `expm1` que toman y devuelven los valores `float` y `long double`.  En un programa C, `expm1` siempre y devuelve `double`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`expm1`, `expm1f`, `expm1l`|\<math.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [exp2, exp2f, exp2l](http://msdn.microsoft.com/es-es/a7974629-be1e-4196-a562-6624a0732003)   
 [pow, powf, powl](../../c-runtime-library/reference/pow-powf-powl.md)