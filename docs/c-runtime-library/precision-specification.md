---
title: "Especificaci&#243;n de precisi&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr100.dll"
  - "msvcr120.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr90.dll"
  - "msvcr80.dll"
apitype: "DLLExport"
f1_keywords: 
  - "c.math"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "printf (función), especificación de formato (campos)"
ms.assetid: dc59ea4e-d23a-4f1f-9881-2c919ebefb82
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Especificaci&#243;n de precisi&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En una especificación de formato, el tercer campo opcional es la especificación de precisión.  Consta de un punto \(.\) seguido de un entero decimal no negativo que, dependiendo del tipo de conversión, especifique el número de caracteres de la cadena, el número de posiciones decimales, o el número de dígitos significativos que se generarán.  
  
 A diferencia de la especificación de ancho, la especificación de precisión puede producir el truncamiento de valor de salida o el redondeo de un valor de punto flotante.  Si se especifica `precision` como 0 y el valor que se va a convertir es 0, el resultado no es ninguna salida de caracteres, como se muestra en este ejemplo:  
  
 `printf( "%.0d", 0 );      /* No characters output */`  
  
 Si la especificación de precisión es un asterisco \(\*\), un argumento de `int` de la lista de argumentos el valor.  En la lista de argumentos, el argumento de `precision` debe preceder al valor que se, como se muestra en este ejemplo:  
  
 `printf( "%.*f", 3, 3.14159265 );  /* 3.142 output */`  
  
 El tipo determina la interpretación de `precision` o la precisión predeterminada cuando se omite `precision` , como se muestra en la tabla siguiente.  
  
### Cómo tipo del efecto de los valores de precisión  
  
|Tipo|Significado|Valor|  
|----------|-----------------|-----------|  
|`a`, `A`|La precisión especifica el número de dígitos después del punto.|La precisión predeterminada es 6.  Si la precisión es 0, no se imprime ningún separador decimal a menos que se utilice el indicador de `#` .|  
|`c`, `C`|La precisión no tiene ningún efecto.|Se imprime el carácter.|  
|`d`, `i`, `u`, `o`, `x`, `X`|La precisión especifica el número mínimo de dígitos que se imprimirán.  Si el número de dígitos en el argumento es menor que `precision`, el valor de salida se completa en la izquierda con ceros.  El valor no se trunca cuando el número de dígitos supera `precision`.|La precisión predeterminada es 1.|  
|`e`, `E`|La precisión especifica el número de dígitos que se imprimirán después del separador decimal.  Se redondea el dígito impreso pasado.|La precisión predeterminada es 6.  Si `precision` es 0 o un punto \(.\) aparece sin un número que lo sigue, no se imprime ningún separador decimal.|  
|`f`|El valor de precisión especifica el número de dígitos después del separador decimal.  Si aparece un separador decimal, al menos un dígito aparece antes del.  El valor se redondea al número correcto de dígitos.|La precisión predeterminada es 6.  Si `precision` es 0, o si el punto \(.\) aparece sin un número que lo sigue, no se imprime ningún separador decimal.|  
|`g`, `G`|La precisión especifica el número máximo de dígitos significativos impresos.|Se imprimen seis dígitos significativos, y se trunca los ceros finales.|  
|`s`, `S`|La precisión especifica el número máximo de caracteres que se imprimirá.  Los caracteres superior a `precision` no se imprimen.|Se imprimen los caracteres hasta que se encuentra un carácter null.|  
  
## Vea también  
 [printf, \_printf\_l, wprintf, \_wprintf\_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [Sintaxis de especificación de formato: Funciones printf y wprintf](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)   
 [Directivas de marca](../c-runtime-library/flag-directives.md)   
 [printf \(Especificación de ancho\)](../c-runtime-library/printf-width-specification.md)   
 [Especificación de tamaño](../c-runtime-library/size-specification.md)   
 [printf \(Caracteres de campo de tipo\)](../c-runtime-library/printf-type-field-characters.md)