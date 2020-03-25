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
ms.openlocfilehash: 781673582cb2c3086677b05abc6a7eb73eeabdb4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178203"
---
# <a name="inheritance-keywords"></a>Palabras clave de herencia

**Específicos de Microsoft**

```
class [__single_inheritance] class-name;
class [__multiple_inheritance] class-name;
class [__virtual_inheritance] class-name;
```

donde:

*nombre de clase*<br/>
Nombre de la clase que se está declarando.

C++ permite declarar un puntero a un miembro de clase antes de la definición de clase. Por ejemplo:

```cpp
class S;
int S::*p;
```

En el código anterior, `p` se declara como un puntero a un miembro de tipo entero de la clase S. Sin embargo, `class S` aún no se ha definido en este código; solo se ha declarado. Cuando el compilador encuentra un puntero así, debe crear una representación generalizada del puntero. El tamaño de la representación depende del modelo de herencia especificado. Hay cuatro maneras de especificar un modelo de herencia al compilador:

- En el IDE **, en representación de puntero a miembro**

- En la línea de comandos mediante el modificador [/VMG](../build/reference/vmb-vmg-representation-method.md)

- Usar el pragma [pointers_to_members](../preprocessor/pointers-to-members.md)

- Usar las palabras clave de herencia **__single_inheritance**, **__multiple_inheritance**y **__virtual_inheritance**. Esta técnica controla el modelo de herencia clase por clase.

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
>  La misma declaración adelantada de una representación de puntero a miembro de la clase debe aparecer en cada unidad de traducción que declare punteros a miembros de esa clase y la declaración debe aparecer antes de que se declaren los punteros a miembros.

Por compatibilidad con versiones anteriores, **_single_inheritance**, **_multiple_inheritance**y **_virtual_inheritance** son sinónimos de **__single_inheritance**, **__multiple_inheritance**y **__virtual_inheritance** a menos que se especifique la opción del compilador [/za \(deshabilitar extensiones de lenguaje)](../build/reference/za-ze-disable-language-extensions.md) .

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[Palabras clave](../cpp/keywords-cpp.md)
