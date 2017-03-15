---
title: "fpclassify | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fpclassify"
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
apitype: "HeaderDef"
f1_keywords: 
  - "fpclassify"
  - "math/fpclassify"
helpviewer_keywords: 
  - "fpclassify (macro)"
  - "fpclassify (función)"
ms.assetid: bf549499-7ff9-4a58-8692-f2d1cb6bab81
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# fpclassify
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve la clasificación del argumento de punto flotante.  
  
## Sintaxis  
  
```  
int fpclassify(   
   /* floating-point */ x   
);  
  
int fpclassify(   
   float x   
); // C++ only  
  
int fpclassify(   
   double x   
); // C++ only  
  
int fpclassify(   
   long double x   
); // C++ only  
  
```  
  
#### Parámetros  
 `x`  
 Valor de punto flotante que se va a probar.  
  
## Valor devuelto  
 `fpclassify` Devuelve un valor entero que indica la clase de punto flotante del argumento `x`. Esta tabla muestra los posibles valores devueltos por `fpclassify`, definido en \< math.h \>.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`FP_NAN`|Un silencioso, señalización o indeterminado NaN|  
|`FP_INFINITE`|Un valor infinito positivo o negativo|  
|`FP_NORMAL`|Un valor distinto de cero normalizado positivo o negativo|  
|`FP_SUBNORMAL`|Un valor positivo o negativo sin normalizar|  
|`FP_ZERO`|Positivo o negativo de valor cero|  
  
## Comentarios  
 En C, `fpclassify` es una macro; en C\+\+, `fpclassify` es una función sobrecargada con tipos de argumento de `float`, `double`, o `long double`. En cualquier caso, el valor devuelto depende del tipo efectiva de la expresión de argumento y no de cualquier representación intermedia. Por ejemplo, normal `double` o `long double` valor puede ser un infinito, desnormalizado, cero o valor cuando se convierte en un `float`.  
  
## Requisitos  
  
|Función o Macro|Encabezado necesario \(C\)|Encabezado necesario \(C\+\+\)|  
|---------------------|--------------------------------|------------------------------------|  
|`fpclassify`|\<math.h\>|\<math.h\> o \<cmath\>|  
  
 El `fpclassify` macro y `fpclassify` funciones que se ajustan a la C99 y especificaciones de C \+\+ 11. Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [isNaN, \_isnan, \_isnanf](../../c-runtime-library/reference/isnan-isnan-isnanf.md)