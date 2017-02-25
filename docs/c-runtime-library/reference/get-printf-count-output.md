---
title: "_get_printf_count_output | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_get_printf_count_output"
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
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "get_printf_count_output"
  - "_get_printf_count_output"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "%n (formato)"
  - "_get_printf_count_output (función)"
  - "get_printf_count_output (función)"
ms.assetid: 850f9f33-8319-433e-98d8-6a694200d994
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# _get_printf_count_output
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Indica si [printf, \_printf\_l, wprintf, \_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)\- las funciones de la familia admiten el formato de `%n` .  
  
## Sintaxis  
  
```  
int _get_printf_count_output();  
```  
  
## Valor devuelto  
 Distinto de cero si se admite `%n` , 0 si `%n` no se admite.  
  
## Comentarios  
 Si `%n` no se admite \(valor predeterminado\), buscar `%n` en la cadena de formato de ninguna de las funciones de `printf` invocará al controlador no válido del parámetro tal como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si se habilita la compatibilidad con `%n` \(vea [\_set\_printf\_count\_output](../../c-runtime-library/reference/set-printf-count-output.md)\) y `%n` se comportará como se describe en [printf \(Caracteres de campo de tipo\)](../../c-runtime-library/printf-type-field-characters.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_get_printf_count_output`|\<stdio.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
 Consulte el ejemplo de [\_set\_printf\_count\_output](../../c-runtime-library/reference/set-printf-count-output.md).  
  
## Equivalente de .NET Framework  
 No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).