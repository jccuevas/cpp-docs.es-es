---
title: Tokens y juegos de caracteres
ms.date: 12/10/2019
helpviewer_keywords:
- Tokens (C++)
- Character sets
- basic source character set (C++)
- universal character names
- basic execution character set (C++)
ms.assetid: 379a2af6-6422-425f-8352-ef0bca6c0d74
ms.openlocfilehash: 1f6dbe2faa6348d61ec00b411cc35e8ef5ceb57a
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301618"
---
# <a name="tokens-and-character-sets"></a>Tokens y juegos de caracteres

El texto de un C++ programa consta de tokens y *espacios en blanco*. Un token es el elemento mínimo de un programa de C++ que es significativo para el compilador. El C++ analizador reconoce estos tipos de tokens:

- [Palabras clave](../cpp/keywords-cpp.md)
- [Identificadores](../cpp/identifiers-cpp.md)
- [Literales numéricos, booleanos y de puntero](../cpp/numeric-boolean-and-pointer-literals-cpp.md)
- [Literales de cadena y carácter](../cpp/string-and-character-literals-cpp.md)
- [Literales definidos por el usuario](../cpp/user-defined-literals-cpp.md)
- [Operadores](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
- [Signos de puntuación](../cpp/punctuators-cpp.md)

Los tokens suelen estar separados por un *espacio en blanco*, que puede ser uno o varios:

- Espacios en blanco
- Tabulaciones horizontales o verticales
- Nuevas líneas
- Fuentes de formularios
- Comentarios

## <a name="basic-source-character-set"></a>Juego básico de caracteres de código fuente

El C++ estándar especifica un *juego básico de caracteres de código fuente* que se puede usar en los archivos de código fuente. Para representar caracteres ajenos a este conjunto, los caracteres adicionales se pueden especificar mediante el uso de un *nombre de carácter universal*. La implementación de MSVC permite caracteres adicionales. El *juego básico de caracteres de código fuente* consta de 96 caracteres que se pueden usar en los archivos de código fuente. Este conjunto incluye el carácter de espacio, tabulación horizontal, tabulación vertical, avance de página y caracteres de control de nueva línea,además del siguiente conjunto de caracteres gráficos:

`a b c d e f g h i j k l m n o p q r s t u v w x y z`

`A B C D E F G H I J K L M N O P Q R S T U V W X Y Z`

`0 1 2 3 4 5 6 7 8 9`

`_ { } [ ] # ( ) < > % : ; . ? * + - / ^ & | ~ ! = , \ " '`

**Específicos de Microsoft**

MSVC incluye el carácter `$` como miembro del juego básico de caracteres de código fuente. MSVC también permite usar un conjunto de caracteres adicional en los archivos de código fuente, en función de la codificación del archivo. De forma predeterminada, Visual Studio almacena archivos de código fuente mediante la página de códigos predeterminada. Cuando se guardan archivos de código fuente mediante una página de códigos específica de la configuración regional o una página de códigos Unicode, MSVC le permite usar cualquiera de los caracteres de esa página de códigos en el código fuente, excepto los códigos de control no permitidos explícitamente en el juego básico de caracteres de código fuente. Por ejemplo, se pueden colocar caracteres de japonés en comentarios, identificadores o literales de cadena, si se guarda el archivo a través de una página de códigos de japonés. MSVC no permite secuencias de caracteres que no se puedan traducir en caracteres multibyte o puntos de código Unicode válidos. Según las opciones del compilador, puede que no todos los caracteres permitidos se muestren en los identificadores. Para obtener más información, vea [Identifiers](../cpp/identifiers-cpp.md).

**FIN de Específicos de Microsoft**

### <a name="universal-character-names"></a>nombres de carácter universal

Dado que los programas de C++ pueden usar muchos más caracteres que los especificados en el juego básico de caracteres de código fuente, es posible especificar estos caracteres de una manera portátil mediante *nombres de carácter universal*. Un nombre de carácter universal consta de una secuencia de caracteres que representan un punto de código Unicode.  Estos tienen dos formatos. Use `\UNNNNNNNN` para representar un punto de código Unicode con el formato U+NNNNNNNN, donde NNNNNNNN es el número de punto de código hexadecimal de ocho dígitos. Use `\uNNNN` de cuatro dígitos para representar un punto de código Unicode con el formato U+0000NNNN.

Los nombres de carácter universal pueden usarse tanto en identificadores como en literales de cadena y carácter. Un nombre de carácter universal no puede usarse para representar un punto de código suplente en el rango de 0xD800 a 0xDFFF. En su lugar, se debe usar el punto de código deseado. El compilador genera automáticamente los suplentes necesarios. Se aplican restricciones adicionales a los nombres de carácter universal que se pueden usar en los identificadores. Para obtener más información, vea [Identifiers](../cpp/identifiers-cpp.md) y [String and Character Literals](../cpp/string-and-character-literals-cpp.md).

**Específicos de Microsoft**

El compilador de Microsoft C++ trata un carácter en forma de nombre de carácter universal y forma literal indistintamente. Por ejemplo, se puede declarar un identificador con formato de nombre de carácter universal y usarlo en el formato de literal:

```cpp
auto \u30AD = 42; // \u30AD is 'キ'
if (キ == 42) return true; // \u30AD and キ are the same to the compiler
```

El formato de caracteres extendidos en el Portapapeles de Windows es específico de la configuración regional de la aplicación. Cortar y pegar estos caracteres en el código desde otra aplicación podría introducir codificaciones de caracteres inesperadas. Esto puede provocar errores de análisis sin causa visible en el código. Se recomienda establecer la codificación del archivo de código fuente en una página de códigos Unicode antes de pegar los caracteres extendidos. También se recomienda usar un IME o la aplicación Mapa de caracteres para generar caracteres extendidos.

**FIN de Específicos de Microsoft**

### <a name="execution-character-sets"></a>Juegos de caracteres de ejecución

Los *juegos de caracteres de ejecución* representan los caracteres y las cadenas que pueden aparecer en un programa compilado. Estos juegos de caracteres constan de todos los caracteres permitidos en un archivo de código fuente, así como los caracteres de control que representan la alerta, el retroceso, el retorno de carro y el carácter nulo. El juego de caracteres de ejecución tiene una representación específica de la configuración regional.
