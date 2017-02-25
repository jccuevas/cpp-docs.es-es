---
title: "NORM, normf, norml1 | Microsoft Docs"
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
  - "norm"
  - "normf"
  - "norml"
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
  - "norm"
  - "normf"
  - "norml"
  - "complex/norm"
  - "complex/normf"
  - "complex/norml"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "norm (función)"
  - "normf (función)"
  - "norml (función)"
ms.assetid: 9786ecfe-0019-4553-b378-0af6c691e15c
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# NORM, normf, norml
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Recupera la magnitud cuadrada de un número complejo.  
  
## Sintaxis  
  
```  
double norm(   
   _Dcomplex z   
);  
float norm(   
   _Fcomplex z   
);  // C++ only  
long double norm(   
  _Lcomplex z   
);  // C++ only  
float normf(   
   _Fcomplex z   
);  
long double norml(   
   _Lcomplex z   
);  
```  
  
#### Parámetros  
 `z`  
 Número complejo.  
  
## Valor devuelto  
 La magnitud del cuadrado `z`.  
  
## Comentarios  
 Como C\+\+ permite las sobrecargas, puede llamar a las sobrecargas de `norm` que toman `_Fcomplex` o `_Lcomplex` valores y devolver `float` o `long double` valores. En un programa de C, `norm` siempre tiene un `_Dcomplex` valor y devuelve un `double` valor.  
  
## Requisitos  
  
|Rutina|Encabezado C|Encabezado C\+\+|  
|------------|------------------|----------------------|  
|`norm`, `normf`, `norml`|\<complex.h\>|\< ccomplex \>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [creal, crealf, creall](../../c-runtime-library/reference/creal-crealf-creall.md)   
 [cproj, cprojf, cprojl](../../c-runtime-library/reference/cproj-cprojf-cprojl.md)   
 [Conj, conjf, conjl](../../c-runtime-library/reference/conj-conjf-conjl.md)   
 [cimag, cimagf, cimagl](../../c-runtime-library/reference/cimag-cimagf-cimagl.md)   
 [carg, cargf, cargl](../../c-runtime-library/reference/carg-cargf-cargl.md)   
 [Cabs, cabsf, cabsl](../../c-runtime-library/reference/cabs-cabsf-cabsl.md)