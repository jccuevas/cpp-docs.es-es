---
title: "fabs, fabsf, fabsl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fabsf"
  - "fabs"
  - "fabsl"
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
  - "fabs"
  - "fabsf"
  - "fabsl"
  - "math\fabs"
  - "math\fabsf"
  - "math\fabsl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "valores absolutos"
  - "fabsf (función)"
  - "calcular valores absolutos"
  - "fabs (función)"
  - "fabsl (función)"
ms.assetid: 23bca210-f408-4f5e-b46b-0ccaaec31e36
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# fabs, fabsf, fabsl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Calcula el valor absoluto del argumento de punto flotante.  
  
## Sintaxis  
  
```  
double fabs(   
   double x   
);  
float fabs(  
   float x   
); // C++ only  
long double fabs(  
   long double x  
); // C++ only  
float fabsf(   
   float x   
);  
long double fabsl(  
   long double x  
);  
```  
  
#### Parámetros  
 `x`  
 Valor de punto flotante.  
  
## Valor devuelto  
 El `fabs` funciones devuelven el valor absoluto del argumento `x`. No se devuelve ningún error.  
  
|Entrada|Excepción SEH|Excepción de Matherr|  
|-------------|-------------------|--------------------------|  
|± QNAN,IND|ninguna|\_DOMAIN|  
  
## Comentarios  
 C\+\+ permite las sobrecargas, puede llamar a las sobrecargas de `fabs` Si incluye el encabezado \< cmath \>. En un programa de C, `fabs` siempre toma y devuelve un tipo double.  
  
## Requisitos  
  
|Función|Encabezado necesario de C|Encabezado de C\+\+ necesario|  
|-------------|-------------------------------|-----------------------------------|  
|`fabs`, `fabsf`, `fabsl`|\<math.h\>|\< cmath \> o \< math.h \>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
 Vea el ejemplo de [abs](../../c-runtime-library/reference/abs-labs-llabs-abs64.md).  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [ABS, laboratorios, llabs, \_abs64](../../c-runtime-library/reference/abs-labs-llabs-abs64.md)   
 [\_cabs](../../c-runtime-library/reference/cabs.md)   
 [labs, llabs](../../misc/labs-llabs.md)