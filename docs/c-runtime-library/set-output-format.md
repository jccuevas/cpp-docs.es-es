---
title: "_set_output_format | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_set_output_format"
apilocation: 
  - "msvcrt.dll"
  - "msvcr120.dll"
  - "msvcr100.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr90.dll"
  - "msvcr110.dll"
  - "msvcr80.dll"
apitype: "DLLExport"
f1_keywords: 
  - "set_output_format"
  - "_set_output_format"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_set_output_format (función)"
  - "_TWO_DIGIT_EXPONENT (constante)"
  - "formato de salida"
  - "set_output_format (función)"
  - "TWO_DIGIT_EXPONENT (constante)"
ms.assetid: 1cb48df8-44b4-4400-bd27-287831d6b3ff
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# _set_output_format
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Personaliza los formatos de salida que usan las funciones de E\/S con formato.  
  
> [!IMPORTANT]
>  Esta función está obsoleta. A partir de Visual Studio 2015, no está disponible en CRT.  
  
## Sintaxis  
  
```  
unsigned int _set_output_format(  
   unsigned int format  
);  
```  
  
#### Parámetros  
 \[in\] `format`  
 Un valor que representa el formato que se utilizará.  
  
## Valor devuelto  
 El formato de salida anterior.  
  
## Comentarios  
 `_set_output_format` se utiliza para configurar la salida de las funciones de E\/S con formato como [printf\_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md). En la actualidad, la única convención de formato que esta función puede cambiar es el número de dígitos que se muestran en los exponentes de la salida de números de punto flotante.  
  
 De forma predeterminada, la salida de números de punto flotante con funciones como `printf_s`, `wprintf_s` y funciones relacionadas de la biblioteca de C estándar de Visual C\+\+ imprime tres dígitos del exponente, incluso aunque no se requieran tres dígitos para representar el valor del exponente. Se utilizan ceros para rellenar el valor hasta los tres dígitos.`_set_output_format` le permite cambiar este comportamiento para que solo se impriman dos dígitos en el exponente, a menos que sea necesario un tercer dígito debido al tamaño del exponente.  
  
 Para habilitar los exponentes de dos dígitos, llame a esta función con el parámetro `_TWO_DIGIT_EXPONENT`, como se muestra en el ejemplo. Para deshabilitar los exponentes de dos dígitos, llame a esta función con un argumento de 0.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_set_output_format`|\<stdio.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../c-runtime-library/compatibility.md) en la Introducción.  
  
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Ejemplo  
  
```  
// crt_set_output_format.c #include <stdio.h> void printvalues(double x, double y) { printf_s("%11.4e %11.4e\n", x, y); printf_s("%11.4E %11.4E\n", x, y); printf_s("%11.4g %11.4g\n", x, y); printf_s("%11.4G %11.4G\n", x, y); } int main() { double x = 1.211E-5; double y = 2.3056E-112; unsigned int old_exponent_format; // Use the default format printvalues(x, y); // Enable two-digit exponent format old_exponent_format = _set_output_format(_TWO_DIGIT_EXPONENT); printvalues(x, y); // Disable two-digit exponent format _set_output_format( old_exponent_format ); printvalues(x, y); }  
```  
  
```Output  
1.2110e-005 2.3056e-112 1.2110E-005 2.3056E-112 1.211e-005  2.306e-112 1.211E-005  2.306E-112 1.2110e-05 2.3056e-112 1.2110E-05 2.3056E-112 1.211e-05  2.306e-112 1.211E-05  2.306E-112 1.2110e-005 2.3056e-112 1.2110E-005 2.3056E-112 1.211e-005  2.306e-112 1.211E-005  2.306E-112  
```  
  
## Vea también  
 [printf\_s, \_printf\_s\_l, wprintf\_s, \_wprintf\_s\_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)   
 [printf \(Caracteres de campo de tipo\)](../c-runtime-library/printf-type-field-characters.md)   
 [\_get\_output\_format](../c-runtime-library/get-output-format.md)