---
title: final (especificador)
ms.date: 11/04/2016
f1_keywords:
- final_CPP
helpviewer_keywords:
- final Identifier
ms.assetid: 649866d0-79d4-449f-ab74-f84b911b79a3
ms.openlocfilehash: 93e8d9b0b445d1120ec15911eb763ae1d7d2d359
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188667"
---
# <a name="final-specifier"></a>final (especificador)

Puede usar la palabra clave **final** para designar funciones virtuales que no se pueden invalidar en una clase derivada. También puede utilizarla para designar clases que no se pueden heredar.

## <a name="syntax"></a>Sintaxis

```
function-declaration final;
class class-name final base-classes
```

## <a name="remarks"></a>Observaciones

**final** es contextual y tiene un significado especial solo cuando se utiliza después de una declaración de función o un nombre de clase. de lo contrario, no es una palabra clave reservada.

Cuando se usa **final** en las declaraciones de clase, `base-classes` es una parte opcional de la declaración.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se usa la palabra clave **final** para especificar que una función virtual no se puede invalidar.

```cpp
class BaseClass
{
    virtual void func() final;
};

class DerivedClass: public BaseClass
{
    virtual void func(); // compiler error: attempting to
                         // override a final function
};
```

Para obtener información sobre cómo especificar que se pueden invalidar las funciones miembro, vea [especificador de invalidación](../cpp/override-specifier.md).

En el ejemplo siguiente se usa la palabra clave **final** para especificar que una clase no se puede heredar.

```cpp
class BaseClass final
{
};

class DerivedClass: public BaseClass // compiler error: BaseClass is
                                     // marked as non-inheritable
{
};
```

## <a name="see-also"></a>Consulte también

[Palabras clave](../cpp/keywords-cpp.md)<br/>
[override (Especificador)](../cpp/override-specifier.md)
