---
title: Espacios de nombres
ms.date: 11/04/2016
helpviewer_keywords:
- union keyword [C], tags
- enumeration tags
- structure tags
- names [C++], declared elements
- name spaces [C++]
- tags, structure tags
- union keyword [C]
ms.assetid: b4bda1d1-cb5e-4f60-ac2b-29af93d8a9a2
ms.openlocfilehash: 76ad9b797a4f192e8f22f8c040f5a308371a461b
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148418"
---
# <a name="name-spaces"></a>Espacios de nombres

El compilador configura “espacios de nombres” para distinguir entre los identificadores utilizados para los diferentes tipos de elementos. Los nombres de cada espacio de nombres deben ser únicos para evitar conflictos, pero un nombre idéntico puede aparecer en más de un espacio de nombres. Esto significa que se puede utilizar el mismo identificador para dos o más elementos diferentes, siempre que los elementos estén en diferentes espacios de nombres. El compilador puede resolver referencias en función del contexto sintáctico del identificador en el programa.

> [!NOTE]
> No confunda la noción limitada de C de un espacio de nombres con la característica “espacio de nombres” de C++. Consulte [Espacios de nombres](../cpp/namespaces-cpp.md) en la Referencia del lenguaje C++ para más información.

En esta lista se describen los espacios de nombres utilizados en C.

Etiquetas de instrucción: las etiquetas de instrucción con nombre forman parte de instrucciones. Las definiciones de las etiquetas de instrucción van seguidas siempre de un signo de dos puntos pero no siempre forman parte de las etiquetas **case**. Los usos de etiquetas de instrucción siempre siguen inmediatamente a la palabra clave **goto**. Las etiquetas de instrucción no tienen que ser distintas de otros nombres o de nombres de etiqueta de otras funciones.

Etiquetas de estructura, unión y enumeración: estas etiquetas forman parte de los especificadores de tipo de estructura, unión y enumeración y, si están presentes, siempre siguen inmediatamente a las palabras reservadas **struct**, **union**, o **enum**. Los nombres de etiqueta deben ser distintos del resto de las etiquetas de estructura, enumeración o unión con la misma visibilidad.

Miembros de estructuras o uniones: los nombres de miembro se asignan en espacios de nombres asociados a cada tipo de estructura y unión. Es decir, el mismo identificador puede ser un nombre de componente en cualquier número de estructuras o de uniones al mismo tiempo. Las definiciones de nombres de componentes siempre aparecen dentro de especificadores de estructura o tipo de unión. Los usos de nombres de componente siempre siguen inmediatamente a los operadores de selección de miembros (**->** y **.**). El nombre de un miembro debe ser único dentro de la estructura o unión, pero no tiene que ser distinto de otros nombres del programa, incluidos los nombres de los miembros de diferentes estructuras y uniones o el nombre de la propia estructura.

Identificadores normales: el resto de los nombres pertenecen a un espacio de nombres que incluye variables, funciones (incluyendo parámetros formales y variables locales) y constantes de enumeración. Los nombres de identificador tienen visibilidad anidada, por lo que puede volver a definirlos dentro de bloques.

Nombres de typedef: los nombres de typedef no se pueden utilizar como identificadores en el mismo ámbito.

Por ejemplo, dado que las etiquetas de estructura, los miembros de estructura y los nombres de variable están en tres espacios de nombres diferentes, los tres elementos denominados `student` en este ejemplo no están en conflicto. El contexto de cada elemento permite la interpretación correcta de cada aparición de `student` en el programa. (Para obtener información sobre las estructuras, vea [Declaraciones de estructura](../c-language/structure-declarations.md)).

```C
struct student {
   char student[20];
   int class;
   int id;
   } student;
```

Cuando `student` aparece después de la palabra clave **struct**, el compilador la reconoce como una etiqueta de estructura. Cuando `student` aparece después de un operador de selección de miembros (**->** o **.**), el nombre hace referencia al miembro de estructura. En otros contextos, `student` hace referencia a la variable de estructura. Sin embargo, no se recomienda sobrecargar el espacio de nombres de etiqueta porque se oculta el significado.

## <a name="see-also"></a>Vea también

[Estructura del programa](../c-language/program-structure.md)
