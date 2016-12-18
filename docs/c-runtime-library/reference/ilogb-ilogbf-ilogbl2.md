---
title: "ilogb, ilogbf, ilogbl | Microsoft Docs"
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
  - "ilogb"
  - "ilogbf"
  - "ilogbl"
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
  - "ilogb"
  - "ilogbf"
  - "ilogbl"
  - "math/ilogb"
  - "math/ilogbf"
  - "math/ilogbl"
helpviewer_keywords: 
  - "ilogb (función)"
  - "ilogbf (función)"
  - "ilogbl (función)"
ms.assetid: 9ef19d57-1caa-41d5-8233-2faad3562fcb
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ilogb, ilogbf, ilogbl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Recupera un entero que representa al exponente imparcial de base 2 del valor especificado.  
  
## Sintaxis  
  
```  
int ilogb(  
   double x  
);  
  
int ilogb(  
   float x  
); //C++ only  
  
int ilogb(  
   long double x  
); //C++ only  
  
int ilogbf(  
   float x  
);  
  
int ilogbl(  
   long double x  
);  
  
```  
  
#### Parámetros  
 \[in\] `x`  
 Valor especificado.  
  
## Valor devuelto  
 Si se realiza correctamente, devuelve el exponente de base 2 de `x` como signo `int` valor.  
  
 De lo contrario, devuelve uno de los valores siguientes, definidos en \< math.h \>:  
  
|Entrada|Resultado|  
|-------------|---------------|  
|±0|FP\_ILOGB0|  
|±inf, ±nan, indefinido|FP\_ILOGBNAN|  
  
 Los errores se notifican como se especifica en [\_matherr](../../c-runtime-library/reference/matherr.md).  
  
## Comentarios  
 Como C\+\+ permite las sobrecargas, puede llamar a las sobrecargas de `ilogb` que toman y devuelven los tipos float y double de tiempo. En un programa de C, `ilogb` siempre toma y devuelve un tipo double.  
  
 Llamar a esta función es similar a llamar al equivalente de `logb` función, a continuación, convertir el valor devuelto a `int`.  
  
## Requisitos  
  
|Rutina|Encabezado C|Encabezado C\+\+|  
|------------|------------------|----------------------|  
|`ilogb`, `ilogbf`,  `ilogbl`|\<math.h\>|\<cmath\>|  
  
 Para obtener información adicional sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [frexp](../../c-runtime-library/reference/frexp.md)   
 [logb, logbf, logbl, \_logb, \_logbf](../../c-runtime-library/reference/logb-logbf-logbl-logb-logbf.md)