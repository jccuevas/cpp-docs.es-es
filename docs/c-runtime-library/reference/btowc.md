---
title: "btowc | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "btowc"
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
  - "api-ms-win-crt-convert-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "btowc"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "btowc (función)"
ms.assetid: 99a46e02-6f86-4569-af79-5feca012add8
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# btowc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Determine si un entero representa un carácter válido de solo\- byte en el estado inicial de cambio.  
  
## Sintaxis  
  
```  
wint_t btowc(  
   int c  
);  
```  
  
#### Parámetros  
 `c`  
 Entero que se va a probar.  
  
## Valor devuelto  
 Devuelve la representación de caracteres anchos de caracteres si el entero representa un carácter válido de solo\- byte en el estado inicial de cambio.  Devuelve WEOF si el entero es EOF o no es un carácter válido de solo\- byte en el estado inicial de cambio.  La configuración regional actual de `LC_TYPE` afecta al resultado de esta función.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`btowc`|\<stdio.h\> o \<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [mbtowc, \_mbtowc\_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)