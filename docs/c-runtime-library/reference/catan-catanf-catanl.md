---
title: "catan, catanf, catanl | Microsoft Docs"
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
  - "catan"
  - "catanf"
  - "catanl"
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
  - "catan"
  - "catanf"
  - "catanl"
  - "complex/catan"
  - "complex/catanf"
  - "complex/catanl"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "catan (función)"
  - "catanf (función)"
  - "catanl (función)"
ms.assetid: 8415ed9c-7909-4d08-b532-4630bafdc7e8
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# catan, catanf, catanl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Recupera el arco tangente de un número complejo con cortes de bifurcación fuera del intervalo \[−1; \+ 1\] en el eje imaginario.  
  
## Sintaxis  
  
```  
_Dcomplex catan(   
   _Dcomplex z   
);  
_Fcomplex catan(   
   _Fcomplex z   
);  // C++ only  
_Lcomplex catan(   
  _Lcomplex z   
);  // C++ only  
_Fcomplex catanf(   
   _Fcomplex z   
);  
_Lcomplex catanl(   
   _Lcomplex z   
);  
```  
  
#### Parámetros  
 `z`  
 Número complejo que representa un ángulo en radianes.  
  
## Valor devuelto  
 El arco tangente de `z`, en radianes. El resultado es ilimitado en el eje imaginario y en el intervalo \[−π\/2; \+ π\/2\] en el eje real.  
  
## Comentarios  
 Puesto que C\+\+ permite las sobrecargas, es posible llamar a las sobrecargas de `catan` que toman y devuelven los valores `_Fcomplex` y `_Lcomplex`. En un programa de C, `catan` siempre toma y devuelve un `_Dcomplex` valor.  
  
## Requisitos  
  
|Rutina|Encabezado C|Encabezado C\+\+|  
|------------|------------------|----------------------|  
|`catan`, `catanf`, `catanl`|\<complex.h\>|\< ccomplex \>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [catanh, catanhf, catanhl](../../c-runtime-library/reference/catanh-catanhf-catanhl.md)   
 [ctanh, ctanhf, ctanhl](../../c-runtime-library/reference/ctanh-ctanhf-ctanhl.md)   
 [csinh, csinhf, csinhl](../../c-runtime-library/reference/csinh-csinhf-csinhl.md)   
 [casinh, casinhf, casinhl](../../c-runtime-library/reference/casinh-casinhf-casinhl.md)   
 [ccosh, ccoshf, ccoshl](../../c-runtime-library/reference/ccosh-ccoshf-ccoshl.md)   
 [cacosh, cacoshf, cacoshl](../../c-runtime-library/reference/cacosh-cacoshf-cacoshl.md)   
 [cacos, cacosf, cacosl](../../c-runtime-library/reference/cacos-cacosf-cacosl.md)   
 [Ctan, ctanf, ctanl](../../c-runtime-library/reference/ctan-ctanf-ctanl.md)   
 [csin, csinf, csinl](../../c-runtime-library/reference/csin-csinf-csinl.md)   
 [casin, casinf, casinl](../../c-runtime-library/reference/casin-casinf-casinl.md)   
 [ccos, ccosf, ccosl](../../c-runtime-library/reference/ccos-ccosf-ccosl.md)   
 [csqrt, csqrtf, csqrtl](../../c-runtime-library/reference/csqrt-csqrtf-csqrtl.md)