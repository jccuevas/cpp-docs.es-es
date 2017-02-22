---
title: "carg, cargf, cargl | Microsoft Docs"
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
  - "carg"
  - "cargf"
  - "cargl"
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
  - "carg"
  - "cargf"
  - "cargl"
  - "complex/carg"
  - "complex/cargf"
  - "complex/cargl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "carg (función)"
  - "cargf (función)"
  - "cargl (función)"
ms.assetid: 610d6a93-b929-46ab-a966-b77db0b804be
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# carg, cargf, cargl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Recupera el argumento de un número complejo, con una bifurcación cortar el eje negativo real.  
  
## Sintaxis  
  
```  
double carg(   
   _Dcomplex z   
);  
float carg(   
   _Fcomplex z   
);  // C++ only  
long double carg(   
   _Lcomplex z   
);  // C++ only  
float cargf(   
   _Fcomplex z   
);  
long double cargl(   
   _Lcomplex z   
);  
```  
  
#### Parámetros  
 `z`  
 Número complejo.  
  
## Valor devuelto  
 El argumento \(también conocida como fase\) de `z`. El resultado está en el intervalo \[−π \+ π\].  
  
## Comentarios  
 Como C\+\+ permite las sobrecargas, puede llamar a las sobrecargas de `carg` que toman `_Fcomplex` o `_Lcomplex` valores y devolver `float` o `long double` valores. En un programa de C, `carg` siempre tiene un `_Dcomplex` valor y devuelve un `double` valor.  
  
## Requisitos  
  
|Rutina|Encabezado C|Encabezado C\+\+|  
|------------|------------------|----------------------|  
|`carg`, `cargf`, `cargl`|\<complex.h\>|\< ccomplex \>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [NORM, normf, norml](../../c-runtime-library/reference/norm-normf-norml1.md)   
 [creal, crealf, creall](../../c-runtime-library/reference/creal-crealf-creall.md)   
 [cproj, cprojf, cprojl](../../c-runtime-library/reference/cproj-cprojf-cprojl.md)   
 [Conj, conjf, conjl](../../c-runtime-library/reference/conj-conjf-conjl.md)   
 [cimag, cimagf, cimagl](../../c-runtime-library/reference/cimag-cimagf-cimagl.md)   
 [Cabs, cabsf, cabsl](../../c-runtime-library/reference/cabs-cabsf-cabsl.md)