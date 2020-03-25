---
title: public (C++)
ms.date: 11/04/2016
f1_keywords:
- public_cpp
helpviewer_keywords:
- public keyword [C++]
ms.assetid: f3e10a59-39f6-4bcd-827e-3e99f8f89497
ms.openlocfilehash: dd45430543ead7258096be8f3d8cef0141f27b4e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179197"
---
# <a name="public-c"></a>public (C++)

## <a name="syntax"></a>Sintaxis

```
public:
   [member-list]
public base-class
```

## <a name="remarks"></a>Observaciones

Cuando precede a una lista de miembros de clase, la palabra clave **Public** especifica que esos miembros son accesibles desde cualquier función. Esto se aplica a todos los miembros declarados hasta el especificador de acceso siguiente o el final de la clase.

Al anteponer el nombre de una clase base, la palabra clave **Public** especifica que los miembros públicos y protegidos de la clase base son miembros públicos y protegidos, respectivamente, de la clase derivada.

El acceso predeterminado de miembros de una clase es privado. El acceso predeterminado de miembros de una estructura o unión es público.

El acceso predeterminado de una clase base es privado para las clases y público para las estructuras. Las uniones no pueden tener clases base.

Para obtener más información, vea [Private](../cpp/private-cpp.md), [Protected](../cpp/protected-cpp.md), [Friend](../cpp/friend-cpp.md)y la tabla de acceso a miembros en [controlar el acceso a los miembros de clase](member-access-control-cpp.md).

## <a name="clr-specific"></a>Específicos de /clr

En los tipos CLR, C++ las palabras clave del especificador de acceso (**Public**, **Private**y **Protected**) pueden afectar a la visibilidad de los tipos y métodos con respecto a los ensamblados. Para obtener más información, vea [Access Control miembro](member-access-control-cpp.md).

> [!NOTE]
>  Los archivos compilados con [/LN](../build/reference/ln-create-msil-module.md) no se ven afectados por este comportamiento. En este caso, todas las clases administradas (ya sean públicas o privadas) estarán visibles.

## <a name="end-clr-specific"></a>Específicos de END /clr

## <a name="example"></a>Ejemplo

```cpp
// keyword_public.cpp
class BaseClass {
public:
   int pubFunc() { return 0; }
};

class DerivedClass : public BaseClass {};

int main() {
   BaseClass aBase;
   DerivedClass aDerived;
   aBase.pubFunc();       // pubFunc() is accessible
                          //    from any function
   aDerived.pubFunc();    // pubFunc() is still public in
                          //    derived class
}
```

## <a name="see-also"></a>Consulte también

[Controlar el acceso a los miembros de clase](member-access-control-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)
