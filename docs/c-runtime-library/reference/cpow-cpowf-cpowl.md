---
title: "cpow, cpowf, cpowl | Microsoft Docs"
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
  - "cpow"
  - "cpowf"
  - "cpowl"
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
  - "cpow"
  - "cpowf"
  - "cpowl"
  - "complex/cpow"
  - "complex/cpowf"
  - "complex/copwl"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "cpow (función)"
  - "cpowf (función)"
  - "complejo/cpowl (función)"
ms.assetid: 83fe2187-22b7-4295-ab16-4d77abdbb80b
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# cpow, cpowf, cpowl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Recupera el valor de un número elevado a la potencia especificada, donde la base y el exponente son números complejos. Esta función tiene una bifurcación cortar el exponente del eje negativo real.  
  
## Sintaxis  
  
```  
_Dcomplex cpow(   
   _Dcomplex x, _Dcomplex y   
);  
_Fcomplex cpow(   
   _Fcomplex x, _Fcomplex y   
);  // C++ only  
_Lcomplex cpow(   
   _Lcomplex x, _Lcomplex y   
);  // C++ only  
_Fcomplex cpowf(   
   _Fcomplex x, _Fcomplex y   
);  
_Lcomplex cpowl(   
   _Lcomplex x, _Lcomplex y   
);  
```  
  
#### Parámetros  
 `x`  
 Base.  
  
 `y`  
 El exponente.  
  
## Valor devuelto  
 El valor de `x` elevado a la potencia de `y` a una bifurcación de cortar para `x` a lo largo del eje negativo real.  
  
## Comentarios  
 Puesto que C\+\+ permite las sobrecargas, es posible llamar a las sobrecargas de `cpow` que toman y devuelven los valores `_Fcomplex` y `_Lcomplex`. En un programa de C, `cpow` siempre toma y devuelve un `_Dcomplex` valor.  
  
## Requisitos  
  
|Rutina|Encabezado C|Encabezado C\+\+|  
|------------|------------------|----------------------|  
|`cpow`, `cpowf`, `cpowl`|\<complex.h\>|\< ccomplex \>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [cexp, cexpf, cexpl](../../c-runtime-library/reference/cexp-cexpf-cexpl.md)   
 [clog10, clog10f, clog10l](../../c-runtime-library/reference/clog10-clog10f-clog10l.md)   
 [CLOG, clogf, clogl](../../c-runtime-library/reference/clog-clogf-clogl.md)