---
title: Juegos de caracteres
ms.date: 05/06/2019
helpviewer_keywords:
- Character sets
- basic source character set (C++)
- universal character names
- basic execution character set (C++)
ms.assetid: 379a2af6-6422-425f-8352-ef0bca6c0d74
ms.openlocfilehash: 92d60e3383abd7e3b3fa2d689958cf02a9b91e75
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222524"
---
# <a name="character-sets"></a>Juegos de caracteres

El texto de un programa de C++ se almacena en archivos de código fuente que usan una codificación de caracteres determinada. El estándar de C++ especifica un juego básico de caracteres de código fuente para los archivos de código fuente y un juego básico de caracteres de ejecución para los archivos compilados. Microsoft C++ compilador (MSVC) permite que un conjunto adicional de caracteres específicos de la configuración regional que se utilizará en archivos de código fuente y los archivos compilados.

## <a name="character-sets"></a>Juegos de caracteres

El estándar de C++ especifica un *juego básico de caracteres de código fuente* que se puede usar en los archivos de código fuente. Para representar caracteres ajenos a este conjunto, los caracteres adicionales se pueden especificar mediante el uso de un *nombre de carácter universal*. Cuando se compila, el *juego básico de caracteres de ejecución* y el *juego básico de caracteres anchos de ejecución* representan los caracteres y las cadenas que pueden aparecer en un programa. La implementación de MSVC permite caracteres adicionales en el código fuente y código compilado.

### <a name="basic-source-character-set"></a>Juego básico de caracteres de código fuente

El *juego básico de caracteres de código fuente* consta de 96 caracteres que pueden usarse en archivos de código fuente. Este conjunto incluye el carácter de espacio, tabulación horizontal, tabulación vertical, avance de página y caracteres de control de nueva línea,además del siguiente conjunto de caracteres gráficos:

`a b c d e f g h i j k l m n o p q r s t u v w x y z`

`A B C D E F G H I J K L M N O P Q R S T U V W X Y Z`

`0 1 2 3 4 5 6 7 8 9`

`_ { } [ ] # ( ) < > % : ; . ? * + - / ^ & | ~ ! = , \ " '`

**Específicos de Microsoft**

MSVC incluye el `$` carácter como un miembro del juego de caracteres básico de origen. MSVC también permite un conjunto adicional de caracteres que se utilizará en archivos de origen, según la codificación del archivo. De forma predeterminada, Visual Studio almacena archivos de código fuente mediante la página de códigos predeterminada. Cuando se guardan los archivos de origen mediante el uso de una página de códigos específicas de configuración regional o una página de códigos Unicode, MSVC le permite usar cualquiera de los caracteres de dicha página de códigos en el código fuente, excepto para los códigos de control no permitidos explícitamente en el carácter de código fuente básicos establecido. Por ejemplo, se pueden colocar caracteres de japonés en comentarios, identificadores o literales de cadena, si se guarda el archivo a través de una página de códigos de japonés. MSVC no admite secuencias de caracteres que no se convierten en caracteres multibyte válidos o puntos de código Unicode. Según las opciones del compilador, puede que no todos los caracteres permitidos se muestren en los identificadores. Para obtener más información, vea [Identifiers](../cpp/identifiers-cpp.md).

**FIN de Específicos de Microsoft**

### <a name="universal-character-names"></a>nombres de carácter universal

Dado que los programas de C++ pueden usar muchos más caracteres que los especificados en el juego básico de caracteres de código fuente, es posible especificar estos caracteres de una manera portátil mediante *nombres de carácter universal*. Un nombre de carácter universal consta de una secuencia de caracteres que representan un punto de código Unicode.  Estos tienen dos formatos. Use `\UNNNNNNNN` para representar un punto de código Unicode con el formato U+NNNNNNNN, donde NNNNNNNN es el número de punto de código hexadecimal de ocho dígitos. Use `\uNNNN` de cuatro dígitos para representar un punto de código Unicode con el formato U+0000NNNN.

Los nombres de carácter universal pueden usarse tanto en identificadores como en literales de cadena y carácter. Un nombre de carácter universal no puede usarse para representar un punto de código suplente en el rango de 0xD800 a 0xDFFF. En su lugar, se debe usar el punto de código deseado. El compilador genera automáticamente los suplentes necesarios. Se aplican restricciones adicionales a los nombres de carácter universal que se pueden usar en los identificadores. Para obtener más información, vea [Identifiers](../cpp/identifiers-cpp.md) y [String and Character Literals](../cpp/string-and-character-literals-cpp.md).

**Específicos de Microsoft**

Microsoft C++ compilador trata un carácter en formato de nombre de carácter universal y forma literal indistintamente. Por ejemplo, se puede declarar un identificador con formato de nombre de carácter universal y usarlo en el formato de literal:

```cpp
auto \u30AD = 42; // \u30AD is 'キ'
if (キ == 42) return true; // \u30AD and キ are the same to the compiler
```

El formato de caracteres extendidos en el Portapapeles de Windows es específico de la configuración regional de la aplicación. Cortar y pegar estos caracteres en el código desde otra aplicación podría introducir codificaciones de caracteres inesperadas. Esto puede provocar errores de análisis sin causa visible en el código. Se recomienda establecer la codificación del archivo de código fuente en una página de códigos Unicode antes de pegar los caracteres extendidos. También se recomienda usar un IME o la aplicación Mapa de caracteres para generar caracteres extendidos.

**FIN de Específicos de Microsoft**

### <a name="basic-execution-character-set"></a>juego básico de caracteres de ejecución

El *juego básico de caracteres de ejecución* y el *juego básico de caracteres anchos de ejecución* constan de todos los caracteres del juego básico de caracteres de código fuente y los caracteres de control que representan los caracteres de alerta, retroceso, retorno de carro y nulo. El *juego de caracteres de ejecución* y el *juego de caracteres anchos de ejecución* son supraconjuntos de los conjuntos básicos. Incluyen los caracteres de código fuente definidos por implementación ajenos al conjunto básico de caracteres de código fuente. El juego de caracteres de ejecución tiene una representación específica de la configuración regional.