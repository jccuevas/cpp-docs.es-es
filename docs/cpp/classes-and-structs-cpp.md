---
title: Clases y structs (C++)
ms.date: 05/07/2019
helpviewer_keywords:
- C++, classes and structs
ms.assetid: 516dd496-13fb-4f17-845a-e9ca45437873
ms.openlocfilehash: 19d95c9519670db39f3ca467aff794233823d7ba
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180893"
---
# <a name="classes-and-structs-c"></a>Clases y structs (C++)

En esta sección se presentan las clases y structs de C++. Las dos construcciones son idénticas en C++, salvo que, en los structs, la accesibilidad predeterminada es pública, mientras que en las clases es privada.

Las clases y los structs son las construcciones con las que define sus propios tipos. Las clases y los structs pueden contener miembros de datos y funciones miembro, lo que permite describir el comportamiento y el estado del tipo.

Se tratan los siguientes temas:

- [class](../cpp/class-cpp.md)

- [struct](../cpp/struct-cpp.md)

- [Información general sobre miembros de clase](../cpp/class-member-overview.md)

- [Control de acceso a miembros](../cpp/member-access-control-cpp.md)

- [Herencia](../cpp/inheritance-cpp.md)

- [Miembros estáticos](../cpp/static-members-cpp.md)

- [Conversiones de tipos definidos por el usuario](../cpp/user-defined-type-conversions-cpp.md)

- [Miembros de datos mutables (especificador mutable)](../cpp/mutable-data-members-cpp.md)

- [Declaraciones de clase anidadas](../cpp/nested-class-declarations.md)

- [Tipos de clase anónima](../cpp/anonymous-class-types.md)

- [Punteros a miembros](../cpp/pointers-to-members.md)

- [this (Puntero)](../cpp/this-pointer.md)

- [Campos de bits de C++](../cpp/cpp-bit-fields.md)

Los tres tipos de clase son estructura, clase, y unión. Se declaran mediante las palabras clave [struct](../cpp/struct-cpp.md), [Class](../cpp/class-cpp.md)y [Union](../cpp/unions.md) . En la tabla siguiente se muestran las diferencias entre los tres tipos de clase.

Para obtener más información sobre las uniones, vea [uniones](../cpp/unions.md). Para obtener información sobre las clases y los C++Structs C++en/CLI y/CX, vea [clases y Structs](../extensions/classes-and-structs-cpp-component-extensions.md).

### <a name="access-control-and-constraints-of-structures-classes-and-unions"></a>Control de acceso y restricciones de las estructuras, clases y uniones

|Estructuras|Clases|Uniones|
|----------------|-------------|------------|
|la clave de clase es **struct**|la clave de clase es **Class**|la clave de clase es **Union**|
|El acceso predeterminado es público|El acceso predeterminado es privado|El acceso predeterminado es público|
|No hay ninguna restricción de uso|No hay ninguna restricción de uso|Usan solo un miembro cada vez|

## <a name="see-also"></a>Consulte también

[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)
