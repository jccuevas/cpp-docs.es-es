---
title: "csinh, csinhf, csinhl | Microsoft Docs"
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
  - "csinh"
  - "csinhf"
  - "csinhl"
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
  - "csinh"
  - "csinhf"
  - "csinhl"
  - "complex/csinh"
  - "complex/csinhf"
  - "complex/csinhl"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "csinh (función)"
  - "csinhf (función)"
  - "csinhl (función)"
ms.assetid: cc616e55-d14d-4cd3-91f0-fbee03ce5edf
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# csinh, csinhf, csinhl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Recupera el seno hiperbólico de un número complejo.  
  
## Sintaxis  
  
```  
_Dcomplex csinh(   
   _Dcomplex z   
);  
_Fcomplex csinh(   
   _Fcomplex z   
);  // C++ only  
_Lcomplex csinh(   
   _Lcomplex z   
);  // C++ only  
_Fcomplex csinhf(   
   _Fcomplex z   
);  
_Lcomplex csinhl(   
   _Lcomplex z   
);  
```  
  
#### Parámetros  
 `z`  
 Número complejo que representa un ángulo en radianes.  
  
## Valor devuelto  
 El seno hiperbólico de `z`, en radianes.  
  
## Comentarios  
 Puesto que C\+\+ permite las sobrecargas, es posible llamar a las sobrecargas de `csinh` que toman y devuelven los valores `_Fcomplex` y `_Lcomplex`. En un programa de C, `csinh` siempre toma y devuelve un `_Dcomplex` valor.  
  
## Requisitos  
  
|Rutina|Encabezado C|Encabezado C\+\+|  
|------------|------------------|----------------------|  
|`csinh`, `csinhf`, `csinhl`|\<complex.h\>|\< ccomplex \>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [catanh, catanhf, catanhl](../../c-runtime-library/reference/catanh-catanhf-catanhl.md)   
 [ctanh, ctanhf, ctanhl](../../c-runtime-library/reference/ctanh-ctanhf-ctanhl.md)   
 [catan, catanf, catanl](../../c-runtime-library/reference/catan-catanf-catanl.md)   
 [casinh, casinhf, casinhl](../../c-runtime-library/reference/casinh-casinhf-casinhl.md)   
 [ccosh, ccoshf, ccoshl](../../c-runtime-library/reference/ccosh-ccoshf-ccoshl.md)   
 [cacosh, cacoshf, cacoshl](../../c-runtime-library/reference/cacosh-cacoshf-cacoshl.md)   
 [cacos, cacosf, cacosl](../../c-runtime-library/reference/cacos-cacosf-cacosl.md)   
 [Ctan, ctanf, ctanl](../../c-runtime-library/reference/ctan-ctanf-ctanl.md)   
 [csin, csinf, csinl](../../c-runtime-library/reference/csin-csinf-csinl.md)   
 [casin, casinf, casinl](../../c-runtime-library/reference/casin-casinf-casinl.md)   
 [ccos, ccosf, ccosl](../../c-runtime-library/reference/ccos-ccosf-ccosl.md)   
 [csqrt, csqrtf, csqrtl](../../c-runtime-library/reference/csqrt-csqrtf-csqrtl.md)