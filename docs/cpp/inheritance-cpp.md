---
title: Herencia (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- derived classes [C++]
- derived classes [C++], about derived classes
- classes [C++], derived
ms.assetid: 3534ca19-d9ed-4a40-be1b-b921ad0e6956
ms.openlocfilehash: 214900f8f36de0fa90ffcd6ca75f3a4e6e2c0777
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178267"
---
# <a name="inheritance--c"></a>Herencia (C++)

En esta sección se explica cómo utilizar clases derivadas para crear programas extensibles.

## <a name="overview"></a>Información general

Las clases nuevas pueden derivarse de clases existentes mediante un mecanismo denominado "herencia" (vea la información que comienza en una [herencia única](../cpp/single-inheritance.md)). Las clases que se utilizan para la derivación se conocen como "clases base" de una clase derivada determinada. Una clase derivada se declara mediante la sintaxis siguiente:

```cpp
class Derived : [virtual] [access-specifier] Base
{
   // member list
};
class Derived : [virtual] [access-specifier] Base1,
   [virtual] [access-specifier] Base2, . . .
{
   // member list
};
```

Detrás de la etiqueta (nombre) de la clase, aparece un carácter de dos puntos seguido de una lista de especificaciones bases.  Las clases base designadas de esta forma deben haberse declarado previamente.  Las especificaciones base pueden contener un especificador de acceso, que es una de las palabras clave **Public**, **Protected** o **Private**.  Estos especificadores de acceso aparecen delante del nombre de la clase base y solo se aplican a esa clase base.  Estos especificadores controlan el permiso de la clase derivada para su uso en miembros de la clase base.  Vea [Access Control de miembro](../cpp/member-access-control-cpp.md) para obtener información sobre el acceso a miembros de clase base.  Si se omite el especificador de acceso, el acceso a la base se considera **privado**.  Las especificaciones base pueden contener la palabra clave **virtual** para indicar la herencia virtual.  Esta palabra clave puede aparecer delante o detrás del especificador de acceso, si hay alguno.  Si se usa la herencia virtual, la clase base se conoce como clase base virtual.

Se pueden especificar varias clases base, separadas por comas.  Si se especifica una sola clase base, el modelo de herencia es una [herencia única](../cpp/single-inheritance.md). Si se especifica más de una clase base, el modelo de herencia se denomina [herencia múltiple](../cpp/multiple-base-classes.md).

Se tratan los siguientes temas:

- [Herencia única](../cpp/single-inheritance.md)

- [Varias clases base](../cpp/multiple-base-classes.md)

- [Funciones virtuales](../cpp/virtual-functions.md)

- [Invalidaciones explícitas](../cpp/explicit-overrides-cpp.md)

- [Clases abstractas](../cpp/abstract-classes-cpp.md)

- [Resumen de reglas de ámbito](../cpp/summary-of-scope-rules.md)

Las palabras clave [__super](../cpp/super.md) y [__interface](../cpp/interface.md) se documentan en esta sección.

## <a name="see-also"></a>Consulte también

[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)
