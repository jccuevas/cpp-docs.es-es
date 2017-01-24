---
title: "Juegos de caracteres | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
helpviewer_keywords: 
  - "Juegos de caracteres"
  - "juego básico de caracteres de código fuente [C++]"
  - "nombres de carácter universal"
  - "juego básico de caracteres de ejecución (C++)"
ms.assetid: 379a2af6-6422-425f-8352-ef0bca6c0d74
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Juegos de caracteres
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El texto de un programa de C\+\+ se almacena en archivos de código fuente que usan una codificación de caracteres determinada. El estándar de C\+\+ especifica un juego básico de caracteres de código fuente para los archivos de código fuente y un juego básico de caracteres de ejecución para los archivos compilados. Visual C\+\+ permite usar un juego adicional de caracteres específicos de la configuración regional en los archivos de código fuente y los archivos compilados.  
  
## Juegos de caracteres  
 El estándar de C\+\+ especifica un *juego básico de caracteres de código fuente* que se puede usar en los archivos de código fuente. Para representar caracteres ajenos a este conjunto, los caracteres adicionales se pueden especificar mediante el uso de un *nombre de carácter universal*. Cuando se compila, el *juego básico de caracteres de ejecución* y el *juego básico de caracteres anchos de ejecución* representan los caracteres y las cadenas que pueden aparecer en un programa. La implementación de Visual C\+\+ permite caracteres adicionales en el código fuente y el código compilado.  
  
### Juego básico de caracteres de código fuente  
 El *juego básico de caracteres de código fuente* consta de 96 caracteres que pueden usarse en archivos de código fuente. Este conjunto incluye el carácter de espacio, tabulación horizontal, tabulación vertical, avance de página y caracteres de control de nueva línea,además del siguiente conjunto de caracteres gráficos:  
  
 `a b c d e f g h i j k l m n o p q r s t u v w x y z`  
  
 `A B C D E F G H I J K L M N O P Q R S T U V W X Y Z`  
  
 `0 1 2 3 4 5 6 7 8 9`  
  
 `_ { } [ ] # ( ) < > % : ; . ? * + - / ^ & | ~ ! = , \ " '`  
  
 **Específicos de Microsoft**  
  
 Visual C\+\+ incluye el carácter `$` como miembro del juego básico de caracteres de código fuente. Visual C\+\+ también permite usar un conjunto adicional de caracteres en archivos de código fuente, según la codificación del archivo. De forma predeterminada, Visual Studio almacena archivos de código fuente mediante la página de códigos predeterminada. Al guardar los archivos de código fuente mediante una página de códigos específicos de la configuración regional o una página de códigos Unicode, Visual C\+\+ permite usar cualquiera de los caracteres de dicha página en el código fuente, excepto los códigos de control no permitidos explícitamente en el juego básico caracteres de código fuente. Por ejemplo, se pueden colocar caracteres de japonés en comentarios, identificadores o literales de cadena, si se guarda el archivo a través de una página de códigos de japonés. Visual C\+\+ no permite las secuencias de caracteres que no pueden convertirse en caracteres multibyte o puntos de código Unicode válidos. Según las opciones del compilador, puede que no todos los caracteres permitidos se muestren en los identificadores. Para obtener más información, vea [Identificadores de C\+\+](../cpp/identifiers-cpp.md).  
  
 **FIN de Específicos de Microsoft**  
  
### Nombres de carácter universal  
 Dado que los programas de C\+\+ pueden usar muchos más caracteres que los especificados en el juego básico de caracteres de código fuente, es posible especificar estos caracteres de una manera portátil mediante *nombres de carácter universal*. Un nombre de carácter universal consta de una secuencia de caracteres que representan un punto de código Unicode.  Estos tienen dos formatos. Use `\UNNNNNNNN` para representar un punto de código Unicode con el formato U\+NNNNNNNN, donde NNNNNNNN es el número de punto de código hexadecimal de ocho dígitos. Use `\uNNNN` de cuatro dígitos para representar un punto de código Unicode con el formato U\+0000NNNN.  
  
 Los nombres de carácter universal pueden usarse tanto en identificadores como en literales de cadena y carácter. Un nombre de carácter universal no puede usarse para representar un punto de código suplente en el rango de 0xD800 a 0xDFFF. En su lugar, se debe usar el punto de código deseado. El compilador genera automáticamente los suplentes necesarios. Se aplican restricciones adicionales a los nombres de carácter universal que se pueden usar en los identificadores. Para obtener más información, vea [Identificadores de C\+\+](../cpp/identifiers-cpp.md) y [Literales de cadena y carácter](../cpp/string-and-character-literals-cpp.md).  
  
 **Específicos de Microsoft**  
  
 El compilador de Visual C\+\+ trata indistintamente un carácter con el formato de nombre de carácter universal y con formato de literal. Por ejemplo, se puede declarar un identificador con formato de nombre de carácter universal y usarlo en el formato de literal:  
  
```cpp  
auto \u30AD = 42; // \u30AD is 'キ' if (キ == 42) return true; // \u30AD and キ are the same to the compiler  
  
```  
  
 El formato de caracteres extendidos en el Portapapeles de Windows es específico de la configuración regional de la aplicación. Cortar y pegar estos caracteres en el código desde otra aplicación podría introducir codificaciones de caracteres inesperadas. Esto puede provocar errores de análisis sin causa visible en el código. Se recomienda establecer la codificación del archivo de código fuente en una página de códigos Unicode antes de pegar los caracteres extendidos. También se recomienda usar un IME o la aplicación Mapa de caracteres para generar caracteres extendidos.  
  
 **FIN de Específicos de Microsoft**  
  
### Juego básico de caracteres de ejecución  
 El *juego básico de caracteres de ejecución* y el *juego básico de caracteres anchos de ejecución* constan de todos los caracteres del juego básico de caracteres de código fuente y los caracteres de control que representan los caracteres de alerta, retroceso, retorno de carro y nulo.   El *juego de caracteres de ejecución* y el *juego de caracteres anchos de ejecución* son supraconjuntos de los conjuntos básicos. Incluyen los caracteres de código fuente definidos por implementación ajenos al conjunto básico de caracteres de código fuente. El juego de caracteres de ejecución tiene una representación específica de la configuración regional.