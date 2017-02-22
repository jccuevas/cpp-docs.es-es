---
title: "_chgsign, _chgsignf, _chgsignl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_chgsignl"
  - "_chgsign"
  - "_chgsignf"
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
  - "_chgsignf"
  - "chgsign"
  - "_chgsignl"
  - "_chgsign"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_chgsign (función)"
  - "_chgsignf (función)"
  - "_chgsignl (función)"
  - "chgsign (función)"
ms.assetid: a6646f8e-213d-4564-8617-f43bc66f989f
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# _chgsign, _chgsignf, _chgsignl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Invierte el signo de un argumento de punto flotante.  
  
## Sintaxis  
  
```  
double _chgsign(   
   double x   
);  
float _chgsignf(  
   float x   
);  
long double _chgsignl(   
   long double x   
);  
```  
  
#### Parámetros  
 `x`  
 Valor de punto flotante que se va a cambiar.  
  
## Valor devuelto  
 Las funciones `_chgsign` devuelven un valor que es igual al argumento de punto flotante `x`, pero con el signo invertido.  No se devuelve ningún error.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_chgsign`|\<float.h\>|  
|`_chgsignf`, `_chgsignl`|\<math.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [fabs, fabsf, fabsl](../../c-runtime-library/reference/fabs-fabsf-fabsl.md)   
 [copysign, copysignf, copysignl, \_copysign, \_copysignf, \_copysignl](../../c-runtime-library/reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)