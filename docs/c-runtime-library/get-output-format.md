---
title: "_get_output_format | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_get_output_format"
apilocation: 
  - "msvcr110_clr0400.dll"
  - "msvcr100.dll"
  - "msvcr80.dll"
  - "msvcrt.dll"
  - "msvcr90.dll"
  - "msvcr120.dll"
  - "msvcr110.dll"
apitype: "DLLExport"
f1_keywords: 
  - "get_output_format"
  - "_get_output_format"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_get_output_format (función)"
  - "get_output_format (función)"
  - "formato de salida"
ms.assetid: 0ce42f3b-3479-41c4-bcbf-1d21f7ee37e7
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# _get_output_format
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Obtiene el valor actual de la marca del formato de salida.  
  
> [!IMPORTANT]
>  Esta función está obsoleta. A partir de Visual Studio 2015, no está disponible en CRT.  
  
## Sintaxis  
  
```  
unsigned int _get_output_format();  
```  
  
## Valor devuelto  
 El valor actual de la marca del formato de salida.  
  
## Comentarios  
 La marca del formato de salida controla las características de la E\/S con formato. En la actualidad, la marca tiene dos valores posibles: 0 y `_TWO_DIGIT_EXPONENT`. Si se establece `_TWO_DIGIT_EXPONENT`, los números de punto flotante se imprimen solo con dos dígitos en el exponente, a menos el tamaño del exponente requiera un tercer dígito. Si la marca es cero, la salida de punto flotante muestra tres dígitos del exponente, con ceros si es necesario para rellenar el valor hasta los tres dígitos.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_get_output_format`|\<stdio.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../c-runtime-library/compatibility.md) en la Introducción.  
  
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [printf, \_printf\_l, wprintf, \_wprintf\_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [printf\_s, \_printf\_s\_l, wprintf\_s, \_wprintf\_s\_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)   
 [printf \(Caracteres de campo de tipo\)](../c-runtime-library/printf-type-field-characters.md)   
 [\_set\_output\_format](../c-runtime-library/set-output-format.md)