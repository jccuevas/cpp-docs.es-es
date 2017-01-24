---
title: "lrint, lrintf, lrintl, llrint, llrintf, llrintl | Microsoft Docs"
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
  - "lrint"
  - "lrintl"
  - "lrintf"
  - "llrint"
  - "llrintf"
  - "llrintl"
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
  - "lrint"
  - "lrintf"
  - "lrintl"
  - "llrint"
  - "llrintf"
  - "llrintl"
  - "math/lrint"
  - "math/lrintf"
  - "math/lrintl"
  - "math/llrint"
  - "math/llrintf"
  - "math/llrintl"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "lrint (función)"
  - "lrintf (función)"
  - "lrintl (función)"
  - "llrint (función)"
  - "llrintf (función)"
  - "llrintl (función)"
ms.assetid: 28ccd5b3-5e6f-434f-997d-a21d51b8ce7f
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# lrint, lrintf, lrintl, llrint, llrintf, llrintl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Redondea el valor de punto flotante especificado al valor entero más cercano, utilizando el modo de redondeo actual y la dirección.  
  
## Sintaxis  
  
```  
long int lrint(  
   double x  
);  
  
long int lrint(  
   float x  
); //C++ only  
  
long int lrint(  
   long double x  
); //C++ only  
  
long int lrintf(  
   float x  
);  
  
long int lrintl(  
   long double x  
);  
  
long long int llrint(  
   double x  
);  
  
long long int llrint(  
   float x  
); //C++ only  
  
long long int llrint(  
   long double x  
); //C++ only  
  
long long int llrintf(  
   float x  
);  
  
long long int llrintl(  
   long double x  
);  
  
```  
  
#### Parámetros  
 \[in\] `x`  
 valor que se va a redondear.  
  
## Valor devuelto  
 Si se realiza correctamente, devuelve el valor entero redondeado del `x`.  
  
|Problema|Volver|  
|--------------|------------|  
|`x` está fuera del intervalo del tipo de valor devuelto<br /><br /> `x` \= ±∞<br /><br /> `x` \= NaN|Genera FE\_INVALID y devuelve cero \(0\).|  
  
## Comentarios  
 Como C\+\+ permite las sobrecargas, puede llamar a las sobrecargas de `lrint` y `llrint` que toman tipos float y double de tiempo. En un programa de C, `lrint` y `llrint` siempre tienen un valor double.  
  
 Si `x` no representa el equivalente de punto flotante de un valor entero, estas funciones producen FE\_INEXACT.  
  
 **Específicos de Microsoft**: cuando el resultado está fuera del intervalo del tipo de valor devuelto, o cuando el parámetro es un NaN o infinito, el valor devuelto es la implementación definida. El compilador de Microsoft devuelve un valor cero \(0\).  
  
## Requisitos  
  
|Función|Encabezado C|Encabezado C\+\+|  
|-------------|------------------|----------------------|  
|`lrint`, `lrintf`, `lrintl`, `llrint`, `llrintf`, `llrintl`|\<math.h\>|\<cmath\>|  
  
 Para obtener información adicional sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)