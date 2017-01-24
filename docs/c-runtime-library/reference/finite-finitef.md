---
title: "_finite, _finitef | Microsoft Docs"
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
  - "_finite"
  - "_finitef"
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
  - "finite"
  - "_finite"
  - "_finitef"
  - "math/_finite"
  - "math/_finitef"
  - "float/_finite"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "finite (función)"
  - "_finite (función)"
  - "_finitef (función)"
ms.assetid: 5a7d7ca7-befb-4e1f-831d-28713c6eb805
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _finite, _finitef
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Determina si un valor de punto flotante es finito.  
  
## Sintaxis  
  
```  
int _finite(   
   double x   
);  
  
int _finitef(   
   float x   
); /* x64 and ARM/ARM64 only */  
```  
  
#### Parámetros  
 `x`  
 Valor de punto flotante que se va a probar.  
  
## Valor devuelto  
 `_finite` y `_finitef` devuelven un valor distinto de cero si el argumento *x* es finito; es decir, si –INF \< `x` \< \+INF. Devuelve 0 si el argumento es infinito o un valor NaN \(no es un número\).  
  
## Comentarios  
 El `_finite` y `_finitef` funciones son específicos de Microsoft. El `_finitef` función sólo está disponible cuando compila para x86, ARM64 o ARM plataformas.  
  
## Requisitos  
  
|Función|Encabezado necesario \(C\)|Encabezado necesario \(C\+\+\)|  
|-------------|--------------------------------|------------------------------------|  
|`_finite`|\<float.h\> o \<math.h\>|\<float.h\>, \<math.h\>, \<cfloat\> o \<cmath\>|  
|`_finitef`|\<math.h\>|\<math.h\> o \<cmath\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Equivalente en .NET Framework  
 [System::Double::IsInfinity](https://msdn.microsoft.com/en-us/library/system.double.isinfinity.aspx)  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [isNaN, \_isnan, \_isnanf](../../c-runtime-library/reference/isnan-isnan-isnanf.md)   
 [\_fpclass, \_fpclassf](../../c-runtime-library/reference/fpclass-fpclassf.md)