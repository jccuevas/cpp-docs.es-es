---
title: "Concatenación de literales de cadena | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- concatenating strings
- strings [C++], concatenating
ms.assetid: 51486b1f-4b1e-4061-9add-1aa38c6cdb3c
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5974e192e32c612fe995cbc736e703f6168a3e8d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="string-literal-concatenation"></a>Concatenación de literales de cadena
Para formar literales de cadena que ocupen más de una línea, puede concatenar las dos cadenas. Para ello, inserte una barra diagonal inversa y presione la tecla ENTRAR. La barra diagonal inversa hace que el compilador omita el siguiente carácter de nueva línea. Por ejemplo, el literal de cadena  
  
```  
"Long strings can be bro\  
ken into two or more pieces."  
```  
  
 es idéntico a la cadena  
  
```  
"Long strings can be broken into two or more pieces."  
```  
  
 Puede usar la concatenación de cadenas en cualquier lugar en el que antes utilizaba una barra diagonal inversa seguida de un carácter de nueva línea para escribir cadenas de más de una línea.  
  
 Para forzar una nueva línea dentro de un literal de cadena, escriba la secuencia de escape de nueva línea (**\n**) en el punto de la cadena donde desee que se corte la línea, de la manera siguiente:  
  
```  
"Enter a number between 1 and 100\nOr press Return"  
```  
  
 Como las cadenas pueden empezar en cualquier columna del código fuente y las cadenas largas pueden continuar en cualquier columna de una línea siguiente, puede colocar las cadenas para mejorar la legibilidad del código fuente. En cualquier caso, la representación en pantalla cuando se muestra no se ve afectada. Por ejemplo:  
  
```  
printf_s ( "This is the first half of the string, "  
           "this is the second half ") ;  
```  
  
 Siempre y cuando cada parte de la cadena esté incluida entre comillas dobles, las partes se concatenan y se muestran como una sola cadena. Esta concatenación se produce de acuerdo con la secuencia de eventos durante la compilación especificada por las [fases de conversión](../preprocessor/phases-of-translation.md).  
  
```  
"This is the first half of the string, this is the second half"  
```  
  
 Un puntero de cadena, inicializado como dos literales de cadena distintos separados solo por un espacio en blanco, se almacenan como una sola cadena (los punteros se explican en [Declaraciones de puntero](../c-language/pointer-declarations.md)). Cuando la referencia es correcta, como en el ejemplo siguiente, el resultado es idéntico al del ejemplo anterior:  
  
```  
char *string = "This is the first half of the string, "  
               "this is the second half";  
  
printf_s( "%s" , string ) ;  
```  
  
 En la fase de traducción 6, las secuencias de caracteres multibyte especificadas por cualquier secuencia de literales de cadena adyacentes o literales de cadena ancha adyacentes se concatenan en una sola secuencia de caracteres multibyte. Por tanto, no diseñe programas para permitir la modificación de literales de cadena durante la ejecución. El estándar ANSI C especifica que el resultado de modificar una cadena es indefinido.  
  
## <a name="see-also"></a>Vea también  
 [Literales de cadena de C](../c-language/c-string-literals.md)