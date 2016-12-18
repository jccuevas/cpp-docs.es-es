---
title: "isNaN, _isnan, _isnanf | Microsoft Docs"
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
  - "_isnan"
  - "_isnanf"
  - "isnan"
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
  - "_isnan"
  - "isnan"
  - "math/isnan"
  - "math/_isnan"
  - "math/_isnanf"
  - "_isnanf"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "NAN (no es un número)"
  - "_isnan (función)"
  - "representación de punto flotante IEEE"
  - "No es un número (NAN)"
  - "isnan (función)"
ms.assetid: 391fbc5b-89a4-4fba-997e-68f1131caf82
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# isNaN, _isnan, _isnanf
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Comprueba si un valor de punto flotante no es un número \(NAN\).  
  
## Sintaxis  
  
```  
int isnan(  
   /* floating-point */ x   
); /* C-only macro */  
  
int _isnan(  
   double x   
);  
  
int _isnanf(  
   float x  
); /* x64 only */  
  
template <class T>  
bool isnan(  
   T x  
) throw(); /* C++ only */  
```  
  
#### Parámetros  
 *x*  
 Valor de punto flotante que se va a probar.  
  
## Valor devuelto  
 En C, el `isnan` macro y `_isnan` y `_isnanf` funciones devuelven un valor distinto de cero si el argumento `x` es un NAN; de lo contrario, devuelven 0.  
  
 En C\+\+, el `isnan` plantilla funciones devuelven `true` Si el argumento `x` es un NAN; de lo contrario, devuelven `false`.  
  
## Comentarios  
 C `isnan` \(macro\) y el `_isnan` y `_isnanf` funciones probar el valor de punto flotante *x*, devuelva un valor distinto de cero si *x* no es un valor de número \(NAN\). Un valor NAN se genera cuando el resultado de una operación de punto flotante no se puede representar en formato de punto flotante de IEEE 754 para el tipo especificado. Para obtener información acerca de cómo se representa un valor NAN de salida, consulte [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md).  
  
 Cuando se compila como C\+\+, el `isnan` \(macro\) no está definido y un `isnan` función de plantilla se define en su lugar. Devuelve un valor de tipo `bool` en lugar de un entero.  
  
 El `_isnan` y `_isnanf` funciones son específicos de Microsoft. El `_isnanf` función sólo está disponible cuando se compila para x64.  
  
## Requisitos  
  
|Rutina|Encabezado necesario \(C\)|Encabezado necesario \(C\+\+\)|  
|------------|--------------------------------|------------------------------------|  
|`isnan`, `_isnanf`|\<math.h\>|\<math.h\> o \<cmath\>|  
|`_isnan`|\<float.h\>|\< float.h \> o \< cfloat \>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [\_finite, \_finitef](../../c-runtime-library/reference/finite-finitef.md)   
 [\_fpclass, \_fpclassf](../../c-runtime-library/reference/fpclass-fpclassf.md)