---
title: Palabras clave de herencia
ms.date: 11/04/2016
f1_keywords:
- __multiple_inheritance
- __single_inheritance_cpp
- __virtual_inheritance_cpp
- __virtual_inheritance
- __multiple_inheritance_cpp
- __single_inheritance
helpviewer_keywords:
- __single_inheritance keyword [C++]
- declaring derived classes [C++]
- keywords [C++], inheritance keywords
- __multiple_inheritance keyword [C++]
- __virtual_inheritance keyword [C++]
- inheritance, declaring derived classes
- derived classes [C++], declaring
- inheritance, keywords
ms.assetid: bb810f56-7720-4fea-b8b6-9499edd141df
ms.openlocfilehash: f0aae655540b4d3f9130d9840d77e0abcf270cc2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374101"
---
# <a name="inheritance-keywords"></a>Palabras clave de herencia

**Microsoft Specific**

```
class [__single_inheritance] class-name;
class [__multiple_inheritance] class-name;
class [__virtual_inheritance] class-name;
```

donde:

*nombre-clase*<br/>
Nombre de la clase que se está declarando.

C++ permite declarar un puntero a un miembro de clase antes de la definición de clase. Por ejemplo:

```cpp
class S;
int S::*p;
```

En el código `p` anterior, se declara como un puntero al miembro entero de la clase S. Sin `class S` embargo, todavía no se ha definido en este código; sólo ha sido declarado. Cuando el compilador encuentra un puntero así, debe crear una representación generalizada del puntero. El tamaño de la representación depende del modelo de herencia especificado. Hay cuatro maneras de especificar un modelo de herencia al compilador:

- En el IDE en **Representación de puntero a miembro**

- En la línea de comandos mediante el modificador [/vmg](../build/reference/vmb-vmg-representation-method.md)

- Uso del [pragma pointers_to_members](../preprocessor/pointers-to-members.md)

- Mediante las palabras clave de herencia **__single_inheritance**, **__multiple_inheritance**y **__virtual_inheritance**. Esta técnica controla el modelo de herencia clase por clase.

    > [!NOTE]
    >  Si siempre se declara un puntero a un miembro de una clase después de definir la clase, no se necesita usar ninguna de estas opciones.

Declarar un puntero a un miembro de una clase antes de la definición de clase afecta al tamaño y la velocidad del archivo ejecutable resultante. Cuanto más compleja es la herencia usada por una clase, mayor será el número de bytes necesarios para representar un puntero a un miembro de la clase y cuando mayor es el código necesario para interpretar el puntero. La herencia única es la menos compleja y la herencia virtual la más compleja.

Si se cambia el ejemplo anterior a:

```cpp
class __single_inheritance S;
int S::*p;
```

independientemente de las opciones de la línea de comandos o las pragmas, los punteros a miembros de `class S` usarán la representación más pequeña posible.

> [!NOTE]
> La misma declaración adelantada de una representación de puntero a miembro de la clase debe aparecer en cada unidad de traducción que declare punteros a miembros de esa clase y la declaración debe aparecer antes de que se declaren los punteros a miembros.

Por compatibilidad con versiones anteriores, **_single_inheritance**, **_multiple_inheritance**y **_virtual_inheritance** son sinónimos de **__single_inheritance**, **__multiple_inheritance**y **__virtual_inheritance** a menos que se especifique la opción del compilador [/Za \(Disable language extensions).](../build/reference/za-ze-disable-language-extensions.md)

**END Microsoft Specific**

## <a name="see-also"></a>Consulte también

[Palabras clave](../cpp/keywords-cpp.md)
