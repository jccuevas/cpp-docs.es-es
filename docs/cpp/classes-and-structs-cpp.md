---
title: Clases y structs (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- Visual C++, classes
- structures, C++ classes
- user-defined types
- classes [C++]
- user-defined types, C++ classes
ms.assetid: 516dd496-13fb-4f17-845a-e9ca45437873
ms.openlocfilehash: 44736b9515363d1406b124858f72f12f8f7f552a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50562752"
---
# <a name="classes-and-structs-c"></a>Clases y structs (C++)

En esta sección se presentan las clases y structs de C++. Las dos construcciones son idénticas en C++, salvo que, en los structs, la accesibilidad predeterminada es pública, mientras que en las clases es privada.

Las clases y los structs son las construcciones con las que define sus propios tipos. Las clases y los structs pueden contener miembros de datos y funciones miembro, lo que permite describir el comportamiento y el estado del tipo.

Se incluyen los temas siguientes:

- [class](../cpp/class-cpp.md)

- [struct](../cpp/struct-cpp.md)

- [Información general sobre miembros de clase](../cpp/class-member-overview.md)

- [Control de acceso a miembros](../cpp/member-access-control-cpp.md)

- [Herencia](../cpp/inheritance-cpp.md)

- [Miembros estáticos](../cpp/static-members-cpp.md)

- [Conversiones de tipos definidos por el usuario](../cpp/user-defined-type-conversions-cpp.md)

- [Mutable (especificador mutable) de los miembros de datos](../cpp/mutable-data-members-cpp.md)

- [Declaraciones de clase anidadas](../cpp/nested-class-declarations.md)

- [Tipos de clase anónima](../cpp/anonymous-class-types.md)

- [Punteros a miembros](../cpp/pointers-to-members.md)

- [this (Puntero)](../cpp/this-pointer.md)

- [Campos de bits de C++](../cpp/cpp-bit-fields.md)

Los tres tipos de clase son estructura, clase, y unión. Se declaran mediante la [struct](../cpp/struct-cpp.md), [clase](../cpp/class-cpp.md), y [unión](../cpp/unions.md) palabras clave. En la tabla siguiente se muestran las diferencias entre los tres tipos de clase.

Para obtener más información sobre las uniones, vea [uniones](../cpp/unions.md). Para obtener información sobre las clases administradas y los structs, vea [clases y Structs](../windows/classes-and-structs-cpp-component-extensions.md).

### <a name="access-control-and-constraints-of-structures-classes-and-unions"></a>Control de acceso y restricciones de las estructuras, clases y uniones

|Estructuras|Clases|Uniones|
|----------------|-------------|------------|
|clave de clase es **struct**|clave de clase es **clase**|clave de clase es **union**|
|El acceso predeterminado es público|El acceso predeterminado es privado|El acceso predeterminado es público|
|No hay ninguna restricción de uso|No hay ninguna restricción de uso|Usan solo un miembro cada vez|

## <a name="see-also"></a>Vea también

[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)