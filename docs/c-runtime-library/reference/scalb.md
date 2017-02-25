---
title: "_scalb | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_scalb"
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
  - "scalb"
  - "_scalb"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_scalb (función)"
  - "cálculos exponenciales"
  - "scalb (función)"
ms.assetid: 148cf5a8-b405-44bf-a1f0-7487adba2421
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# _scalb
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Escala el argumento por una potencia de 2.  
  
## Sintaxis  
  
```  
double _scalb(  
   double x,  
   long exp   
);  
```  
  
#### Parámetros  
 `x`  
 De precisión doble, valor de punto flotante.  
  
 `exp`  
 Exponente entero largo.  
  
## Valor devuelto  
 Devuelve un valor exponencial si correctamente.  En desbordamiento \(dependiendo del signo de `x`\), `_scalb` vuelve \+\/\- `HUGE_VAL`; la variable de `errno` se establece en `ERANGE`.  
  
 Para obtener más información sobre estos y otros códigos de retorno, vea [\_doserrno, errno, \_sys\_errlist, y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 La función de `_scalb` calcula el valor de `x *` 2exp.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_scalb`|\<float.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [ldexp](../../c-runtime-library/reference/ldexp.md)