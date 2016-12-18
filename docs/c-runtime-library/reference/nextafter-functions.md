---
title: "nextafter, nextafterf, nextafterl, _nextafter, _nextafterf, nexttoward, nexttowardf, nexttowardl | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "nextafterf"
  - "_nextafterf"
  - "nextafter"
  - "nextafterl"
  - "_nextafter"
  - "nexttoward"
  - "nexttowardf"
  - "nexttowardl"
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
  - "nextafter"
  - "_nextafter"
  - "nextafterf"
  - "nextafterl"
  - "_nextafterf"
  - "math/nextafter"
  - "math/nextafterf"
  - "math/nextafterl"
  - "nexttoward"
  - "nexttowardf"
  - "nexttowardl"
  - "math/nexttoward"
  - "math/nexttowardf"
  - "math/nexttowardl"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_nextafter (función)"
  - "nextafter (función)"
  - "_nextafterf (función)"
  - "nextafterf (función)"
  - "nextafterl (función)"
  - "nexttoward (función)"
  - "nexttowardf (función)"
  - "nexttowardl (función)"
ms.assetid: 9785bfb9-de53-4bd0-9637-f05fa0c1f6ab
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# nextafter, nextafterf, nextafterl, _nextafter, _nextafterf, nexttoward, nexttowardf, nexttowardl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve el siguiente valor de punto flotante puede representar.  
  
## Sintaxis  
  
```  
double nextafter(  
   double x,  
   double y   
);  
  
float nextafter(  
   float x,  
   float y   
); /* C++ only, requires <cmath> */  
  
long double nextafter(  
   long double x,  
   long double y   
); /* C++ only, requires <cmath> */  
  
float nextafterf(  
   float x,  
   float y   
);   
  
long double nextafterl(  
   long double x,  
   long double y   
);  
  
double _nextafter(  
   double x,  
   double y   
);  
  
float _nextafterf(  
   float x,  
   float y   
); /* x64 only */  
  
double nexttoward(  
   double x,  
   long double y   
);  
  
float nexttoward(  
   float x,  
   long double y   
); /* C++ only, requires <cmath> */  
  
long double nexttoward(  
   long double x,  
   long double y   
); /* C++ only, requires <cmath> */  
  
float nexttowardf(  
   float x,  
   long double y   
);   
  
long double nexttowardl(  
   long double x,  
   long double y   
);  
```  
  
#### Parámetros  
 `x`  
 Valor de punto flotante que se va a iniciar desde.  
  
 `y`  
 Valor de punto flotante para ir hacia.  
  
## Valor devuelto  
 Devuelve el siguiente valor de punto flotante puede representar de tipo de valor devuelto después de `x` en la dirección de `y`. Si `x`\=`y`, la función devuelve `y`, convertido en el tipo de valor devuelto con ninguna excepción activada. Si `x` no es igual a `y`, y el resultado es cero o un desnormalizados, se establece el estado de excepción de punto flotante FE\_UNDERFLOW y FE\_INEXACT y se devuelve el resultado correcto. Si el valor `x` o `y` es un NAN, el valor devuelto es uno de los valores de entrada NaN. Si `x` es finito y el resultado es infinito o no se puede representar en el tipo, se devuelve un firmada correctamente infinito ni NAN, se establece el estado de excepción de punto flotante FE\_OVERFLOW y FE\_INEXACT, y `errno` se establece en ERANGE.  
  
## Comentarios  
 El `nextafter` y `nexttoward` familias de función son equivalentes, excepto el tipo de parámetro `y`. Si `x` y `y` son iguales, el valor devuelto es `y` convertir el tipo de valor devuelto.  
  
 Como C\+\+ permite las sobrecargas, si incluye \< cmath \> puede llamar a las sobrecargas de `nextafter` y `nexttoward` que devuelve `float` y `long double` tipos. En un programa de C, `nextafter` y `nexttoward` siempre devuelven `double`.  
  
 El `_nextafter` y `_nextafterf` funciones son específicos de Microsoft. El `_nextafterf` función sólo está disponible cuando se compila para x64.  
  
## Requisitos  
  
|Rutina|Encabezado necesario \(C\)|Encabezado necesario \(C\+\+\)|  
|------------|--------------------------------|------------------------------------|  
|`nextafter`, `nextafterf`, `nextafterl`, `_nextafterf`, `nexttoward`, `nexttowardf`, `nexttowardl`|\<math.h\>|\<math.h\> o \<cmath\>|  
|`_nextafter`|\<float.h\>|\< float.h \> o \< cfloat \>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [isNaN, \_isnan, \_isnanf](../../c-runtime-library/reference/isnan-isnan-isnanf.md)