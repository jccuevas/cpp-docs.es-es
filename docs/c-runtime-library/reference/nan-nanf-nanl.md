---
title: "nan, nanf, nanl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "nanf"
  - "nan"
  - "nanl"
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
  - "nan"
  - "nanl"
  - "nanf"
dev_langs: 
  - "C++"
ms.assetid: 790e9158-80ab-43e0-8f5a-096198553fd9
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# nan, nanf, nanl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve un valor NaN reservado.  
  
## Sintaxis  
  
```  
double nan(    const char* input  ); float nanf(    const char* input  ); long double nanl(    const char* input  );  
```  
  
#### Parámetros  
 `input`  
 Valor de cadena.  
  
## Valor devuelto  
 Las funciones `nan` devuelven un valor NaN reservado.  
  
## Comentarios  
 Las funciones `nan` devuelven un valor de punto flotante que se corresponde con un NaN reservado \(de no señalización\).  El valor `input` se omite.  Para más información sobre cómo se representa un NaN en la salida, vea [printf, \_printf\_l, wprintf, \_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md).  
  
## Requisitos  
  
|Función|Encabezado C|Encabezado C\+\+|  
|-------------|------------------|----------------------|  
|`nan`, `nanf`, `nanl`|\<math.h\>|\<cmath\>|  
  
## Equivalente en .NET Framework  
 [System::Double::NaN](https://msdn.microsoft.com/en-us/library/system.double.nan.aspx)  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [\_finite, \_finitef](../../c-runtime-library/reference/finite-finitef.md)   
 [\_fpclass, \_fpclassf](../../c-runtime-library/reference/fpclass-fpclassf.md)   
 [isNaN, \_isnan, \_isnanf](../../c-runtime-library/reference/isnan-isnan-isnanf.md)