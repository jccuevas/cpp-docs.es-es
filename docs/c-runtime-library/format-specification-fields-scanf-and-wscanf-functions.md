---
title: "Campos de especificaci&#243;n de formato: funciones scanf y wscanf | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr80.dll"
  - "msvcr110.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
apitype: "DLLExport"
f1_keywords: 
  - "wscanf"
  - "scanf"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "ancho, especificaciones de scanf (función)"
  - "especificaciones de formato de scanf"
  - "scanf (especificaciones de ancho)"
  - "scanf (caracteres de campo de tipo)"
  - "campos de tipo, scanf (función)"
  - "campos de especificación de formato para la función scanf"
  - "campos de tipo"
ms.assetid: 7e95de1b-0b71-4de3-9f81-c9560c78e039
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Campos de especificaci&#243;n de formato: funciones scanf y wscanf
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Información aquí se aplica a la familia completa de `scanf` de funciones, incluidas las versiones seguras y describe los símbolos utilizados para indicar a las funciones de `scanf` cómo analizar el flujo de entrada, como el flujo de entrada `stdin` para `scanf`, en los valores que se insertan en variables de programa.  
  
 Una especificación de formato tiene el siguiente formato:  
  
 `%`\[`*`\] \[[ancho](../c-runtime-library/scanf-width-specification.md)\] \[{[h &#124; l &#124; ll &#124; I64 &#124; L](../c-runtime-library/scanf-width-specification.md)}\][type](../c-runtime-library/scanf-type-field-characters.md)  
  
 El argumento de `format` especifica la interpretación de entrada y puede contener uno o más de los siguientes:  
  
-   Caracteres de espacio en blanco: espacio en blanco \(“"\); ficha \(” \\t "\); o línea nueva \(“\\n "\).  Un carácter de espacio en blanco produce `scanf` para leer, pero no lo almacena, todos los caracteres de espacio en blanco consecutivos en la entrada hasta el siguiente carácter del no\-blanco\- espacio.  Un carácter de espacio en blanco en el formato coincide con cualquier número \(0 incluida y combinación de caracteres de espacio en blanco en la entrada.  
  
-   Caracteres de No\-blanco\- espacio, salvo el signo de porcentaje \(`%`\).  Un carácter de no\-blanco\- espacio produce `scanf` para leer, pero no lo almacena, un carácter coincidente del no\-blanco\- espacio.  Si no coincide con el carácter siguiente del flujo de entrada, `scanf` finaliza.  
  
-   Dar formato a las especificaciones, presentadas por el signo de porcentaje \(`%`\).  Una especificación de formato hace `scanf` para leer y convertir los caracteres de la entrada en valores de un tipo especificado.  El valor asignado a un argumento en la lista de argumentos.  
  
 El formato se lee de izquierda a derecha.  Se espera que las especificaciones de formato del extremo de caracteres coinciden con la secuencia de caracteres del flujo de entrada; los caracteres coincidentes en el flujo de entrada se examinan pero no almacenados.  Si un carácter en el flujo de entrada está en conflicto con la especificación de formato, `scanf` termina, y el carácter se deja en el flujo de entrada como si no se hubiera leído.  
  
 Cuando se encuentra la primera especificación de formato, el valor del primer campo de entrada se convierte como esta especificación y almacenado en la ubicación especificada en primer `argument`.  La segunda especificación de formato genera el segundo campo de entrada que se va a convertir y almacenado en segundo `argument`, etc. a través del final de la cadena de formato.  
  
 Un campo de entrada se define como todos los caracteres hasta el primer carácter de espacio en blanco \(espacio, pestaña, o nueva línea\), o hasta el primer carácter que no se puede convertir según la especificación de formato, o hasta el ancho de campo \(si se especifica\) se alcance.  Si hay demasiados argumentos para las especificaciones especificadas, se evalúan pero se omiten los argumentos adicionales.  Los resultados son imprevisibles si no hay suficientes argumentos para la especificación de formato.  
  
 Cada campo de la especificación de formato es un carácter o un número que una opción de formato determinada.  El carácter de `type` , que se produce después de que el campo opcional último de formato, determina si el campo de entrada se interpreta como un carácter, una cadena, o número.  
  
 La especificación más simple de formato contiene únicamente el signo de porcentaje y un carácter de `type` \(por ejemplo, `%s`\).  Si un signo de porcentaje \(`%`\) va seguido de un carácter que no tiene ningún significado como carácter de la formato\- CONTROL, tratan a ese carácter y los caracteres siguientes \(hasta el signo de porcentaje siguiente\) como secuencia normal de caracteres, es decir, una secuencia de caracteres que se deben comparar la entrada.  Por ejemplo, especificar que un carácter de signo debe entrar, utilice `%%`.  
  
 Un asterisco \(`*`\) después del signo de porcentaje suprime la asignación de campos de entrada siguiente, se interpreta que aunque un campo del tipo especificado.  El campo se digitaliza pero no almacenado.  
  
 Las versiones seguras \(las con el sufijo de `_s` \) de la familia de `scanf` de funciones requieren que un parámetro del tamaño del búfer se dedica inmediatamente después de cada parámetro de `c`con tipo, de `C`, de `s`, de `S` o de `[`.  Para obtener más información sobre versiones seguras de la familia de `scanf` de funciones, vea [scanf\_s, \_scanf\_s\_l, wscanf\_s, \_wscanf\_s\_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md).  
  
## Vea también  
 [scanf \(Especificación de ancho\)](../c-runtime-library/scanf-width-specification.md)   
 [scanf \(Caracteres de campo de tipo\)](../c-runtime-library/scanf-type-field-characters.md)   
 [scanf, \_scanf\_l, wscanf, \_wscanf\_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [scanf\_s, \_scanf\_s\_l, wscanf\_s, \_wscanf\_s\_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)