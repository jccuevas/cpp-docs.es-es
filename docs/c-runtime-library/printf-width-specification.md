---
title: "printf (Especificaci&#243;n de ancho) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr110.dll"
  - "msvcr80.dll"
  - "msvcr100.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr90.dll"
  - "msvcr120.dll"
apitype: "DLLExport"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "printf (función), especificación de formato (campos)"
  - "printf (función), especificación de ancho"
ms.assetid: 8b4a1b1e-bf6e-414f-a1b6-a9b6f1b6ce92
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# printf (Especificaci&#243;n de ancho)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En una especificación de formato, el segundo campo opcional es la especificación de ancho.  El argumento de `width` es un entero decimal no negativo que controla el número de caracteres mínimo que se genera.  Si el número de caracteres del valor de salida es menor que el ancho especificado, los espacios en blanco se agregan a la izquierda o derecha del siguiente valor dependencias con si es el indicador izquierdo de alineación \(`-`\) especificar\- hasta alcanzar el ancho mínimo.  Si `width` es precedido por 0, los ceros iniciales se agregan a conversiones de enteros o de punto flotante hasta alcanzar el ancho mínimo, excepto cuando la conversión a un infinito o un NAN.  
  
 La especificación de ancho nunca produce un valor que se truncará.  Si el número de caracteres del valor de salida es mayor que el ancho especificado, o si `width` no se especifica, todos los caracteres del valor, se representa con la especificación de [precisión](../c-runtime-library/precision-specification.md) .  
  
 Si la especificación de ancho es un asterisco \(`*`\), un argumento de `int` de la lista de argumentos el valor.  El argumento de `width` debe preceder al valor que se está dando formato en la lista de argumentos, como se muestra en este ejemplo:  
  
 `printf("%0*f", 5, 3);  /* 00003 is output */`  
  
 Faltan o un valor pequeño de `width` en una especificación de formato no produce el truncamiento de un valor de salida.  Si el resultado de una conversión es más ancho que el valor de `width` , el campo se expande para incluir el resultado de la conversión.  
  
## Vea también  
 [printf, \_printf\_l, wprintf, \_wprintf\_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [Sintaxis de especificación de formato: Funciones printf y wprintf](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)   
 [Directivas de marca](../c-runtime-library/flag-directives.md)   
 [Especificación de precisión](../c-runtime-library/precision-specification.md)   
 [Especificación de tamaño](../c-runtime-library/size-specification.md)   
 [printf \(Caracteres de campo de tipo\)](../c-runtime-library/printf-type-field-characters.md)