---
title: "logb, logbf, logbl, _logb, _logbf | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "logb"
  - "_logb"
  - "_logbl"
  - "logbf"
  - "logbl"
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
  - "logb"
  - "logbl"
  - "_logb"
  - "_logbf"
  - "logbf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_logb (función)"
  - "_logbf (función)"
  - "exponente, números de punto flotante"
  - "exponentes y mantisas"
  - "funciones de punto flotante"
  - "funciones de punto flotante, mantisa y exponente"
  - "logb (función)"
  - "logbf (función)"
  - "logbl (función)"
  - "mantisas, variables de punto flotante"
ms.assetid: 780c4daa-6fe6-4fbc-9412-4c1ba1a1766f
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# logb, logbf, logbl, _logb, _logbf
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Extrae el valor de exponente de un argumento de punto flotante.  
  
## Sintaxis  
  
```  
double logb(  
   double x   
);  
float logb(  
   float x   
); // C++ only  
long double logb(  
   long double x   
); // C++ only   
float logbf(  
   float x   
);  
long double logbl(  
   long double x   
);  
double _logb(  
   double x   
);  
float _logbf(  
   float x   
);  
```  
  
#### Parámetros  
 x  
 Valor de punto flotante.  
  
## Valor devuelto  
 `logb` devuelve el valor de exponente imparcial de `x` en forma de entero con signo representado como un valor de punto flotante.  
  
## Comentarios  
 Las funciones `logb` extraen el valor de exponente del argumento de punto flotante `x`, como si `x` se representara con el intervalo infinito.  Si el argumento `x` es desnormalizado, se trata como si fuera normalizado.  
  
 Puesto que C\+\+ permite las sobrecargas, es posible llamar a las sobrecargas de `logb` que toman y devuelven los valores `float` o `long double`.  En un programa C, `logb` siempre y devuelve `double`.  
  
|Entrada|Excepción SEH|Excepción de Matherr|  
|-------------|-------------------|--------------------------|  
|± QNAN,IND|None|\_DOMAIN|  
|± 0|ZERODIVIDE|\_SING|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_logb`|\<float.h\>|  
|`logb`, `logbf`, `logbl`, `_logbf`|\<math.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [frexp](../../c-runtime-library/reference/frexp.md)