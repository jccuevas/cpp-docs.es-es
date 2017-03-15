---
title: "Sintaxis de especificaci&#243;n de formato: Funciones printf y wprintf | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr90.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr100.dll"
  - "msvcr110.dll"
  - "msvcr80.dll"
  - "msvcr120.dll"
apitype: "DLLExport"
f1_keywords: 
  - "wprintf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "directivas de marca, función printf"
  - "campos de especificación de formato para la función printf"
  - "precisión (campos)"
  - "marca de impresión (directivas)"
  - "printf (función), especificación de formato (campos)"
  - "printf (función), precisión"
  - "campos de tipo"
  - "campos de tipo, printf (función)"
ms.assetid: 664b1717-2760-4c61-bd9c-22eee618d825
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# Sintaxis de especificaci&#243;n de formato: Funciones printf y wprintf
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Describe la sintaxis de los argumentos de cadena de formato de `printf`, `wprintf` y funciones relacionadas.  Existen versiones más seguras de estas funciones; para obtener más información, vea [Características de seguridad de CRT](../c-runtime-library/security-features-in-the-crt.md).  Para obtener información sobre cada una de las funciones individuales, vea la documentación correspondiente.  Para obtener una lista de estas funciones, vea [E\/S de secuencia](../c-runtime-library/stream-i-o.md).  
  
 Una especificación de formato, que consta de campos opcionales y obligatorios, tiene el formato siguiente:  
  
 `%`\[[flags](../c-runtime-library/flag-directives.md)\] \[[width](../c-runtime-library/printf-width-specification.md)\] \[**.**[precision](../c-runtime-library/precision-specification.md)\] \[{`h` &#124; `l` &#124; `ll` &#124; `w` &#124; `I` &#124; `I32` &#124; `I64`}\] [type](../c-runtime-library/printf-type-field-characters.md)  
  
 Cada campo de la especificación de formato es un carácter o un número que indica una opción de formato o un especificador de conversión.  El carácter obligatorio de `type` especifica el tipo de conversión que se aplicará a un argumento.  Los campos opcionales `flags`, `width` y `precision` controlan otras características del formato.  Una especificación de formato básica solo contiene el signo de porcentaje y un carácter de `type`, por ejemplo `%s`, que especifica una conversión de cadena.  En las versiones seguras de las funciones, si un signo de porcentaje va seguido de un carácter que no tiene ningún significado como campo de formato, se invoca el controlador de parámetros no válidos.  Para obtener más información, vea [Validación de parámetros](../c-runtime-library/parameter-validation.md).  En las versiones no seguras, el carácter se copia sin cambios en la salida.  Para imprimir un carácter de signo de porcentaje, use `%%`.  
  
 Los campos de la especificación de formato controlan los siguientes aspectos de la conversión de argumentos y formato:  
  
 `type`  
 Carácter especificador de conversión necesario que determina si el parámetro `argument` asociado se interpreta como un carácter, una cadena, un entero o número de punto flotante.  Para obtener más información, vea [printf \(Caracteres de campo de tipo\)](../c-runtime-library/printf-type-field-characters.md).  
  
 `flags`  
 Carácter o caracteres opcionales que controlan la justificación del resultado, y el resultado de signos, espacios en blanco, ceros iniciales, separadores decimales, y prefijos octales y hexadecimales.  Para obtener más información, vea [Directivas de marca](../c-runtime-library/flag-directives.md).  En una especificación de formato puede haber varias marcas, que pueden aparecer en cualquier orden.  
  
 `width`  
 Número decimal opcional que especifica el número de caracteres mínimo que se genera.  Para obtener más información, vea [printf \(Especificación de ancho\)](../c-runtime-library/printf-width-specification.md).  
  
 `precision`  
 Número decimal opcional que especifica el número máximo de caracteres que se imprime para las cadenas, el número de dígitos significativos o número de dígitos detrás del carácter de separador decimal para valores de punto flotante, o el número mínimo de dígitos que se imprimen para los valores enteros.  Para obtener más información, vea la sección “Efecto de los valores de precisión en el tipo” en [Especificación de precisión](../c-runtime-library/precision-specification.md).  
  
 `h` &#124; `l` &#124; `ll` &#124; `w` &#124; `I` &#124; `I32` &#124; `I64`  
 Prefijos opcionales de `type` que especifican el tamaño del argumento correspondiente.  Para obtener más información, vea “Prefijos de tamaño” en [Especificación de tamaño](../c-runtime-library/size-specification.md).  
  
> [!IMPORTANT]
>  Asegúrese de que las cadenas de especificación de formato no son definidas por el usuario.  Por ejemplo, imagine un programa que solicita al usuario que escriba un nombre y almacena la entrada en una variable de cadena denominada `name`.  Para imprimir `name`, no haga esto:  
>   
>  `printf( name ); /* Danger!  If name contains "%s", program will crash */`  
>   
>  En lugar de ello, haga esto:  
>   
>  `printf( "%s", name );`  
  
## Vea también  
 [printf, \_printf\_l, wprintf, \_wprintf\_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [printf\_s, \_printf\_s\_l, wprintf\_s, \_wprintf\_s\_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)   
 [printf\_p \(Parámetros de posición\)](../c-runtime-library/printf-p-positional-parameters.md)   
 [Directivas de marca](../c-runtime-library/flag-directives.md)   
 [printf \(Especificación de ancho\)](../c-runtime-library/printf-width-specification.md)   
 [Especificación de precisión](../c-runtime-library/precision-specification.md)   
 [Especificación de tamaño](../c-runtime-library/size-specification.md)   
 [printf \(Caracteres de campo de tipo\)](../c-runtime-library/printf-type-field-characters.md)