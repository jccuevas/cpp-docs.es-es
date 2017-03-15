---
title: "nearbyint, nearbyintf, nearbyintl1 | Microsoft Docs"
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
  - "nearbyint"
  - "nearbyintf"
  - "nerabyintl"
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
  - "nearbyint"
  - "nearbyintf"
  - "nearbyintl"
  - "math/nearbyint"
  - "math/narbyintf"
  - "math/narbyintl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "nearbyint (función)"
  - "nearbyintf (función)"
  - "nearbyintl (función)"
ms.assetid: dd39cb68-96b0-434b-820f-6ff2ea65584f
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# nearbyint, nearbyintf, nearbyintl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Redondea el valor de punto flotante especificado en un entero y devuelve ese valor en un formato de punto flotante.  
  
## Sintaxis  
  
```  
double nearbyint(  
   double x  
);  
  
float nearbyint(  
   float x  
); //C++ only  
  
long double nearbyint(  
   long double x  
); //C++ only  
  
float nearbyintf(  
   float x  
);  
  
long double nearbyintl(  
   long double x  
);  
  
```  
  
#### Parámetros  
 \[in\] `x`  
 El valor que se va a redondear.  
  
## Valor devuelto  
 Si se realiza correctamente, devuelve `x`, redondeada al entero más cercano, usando el formato de redondeo actual según se define en fegetround. De lo contrario, la función puede devolver uno de los siguientes valores:  
  
|Problema|Volver|  
|--------------|------------|  
|`x` \= ±INFINITY|±Infinity, sin modificar|  
|`x` \= ±0|± 0, sin modificar|  
|`x` \= NaN|NaN|  
  
 No se notifican a través de [\_matherr](../../c-runtime-library/reference/matherr.md); en concreto, esta función no informa de las excepciones de FE\_INEXACT.  
  
## Comentarios  
 La principal diferencia entre esta función y `rint` es que esta función no genera la excepción de punto flotante inexacto.  
  
 Dado que los valores de punto flotante máximos son enteros exactas, esta función nunca se desborde por sí mismo; en su lugar, la salida puede desbordar el valor devuelto, según la versión de la función que utilice.  
  
## Requisitos  
  
|Función|Encabezado C|Encabezado C\+\+|  
|-------------|------------------|----------------------|  
|`nearbyint`, `nearbyintf`,  `nearbyintl`|\<math.h\>|\<cmath\>|  
  
 Para obtener información adicional sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)