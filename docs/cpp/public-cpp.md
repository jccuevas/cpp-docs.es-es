---
title: public (C++)
ms.date: 11/04/2016
f1_keywords:
- public_cpp
helpviewer_keywords:
- public keyword [C++]
ms.assetid: f3e10a59-39f6-4bcd-827e-3e99f8f89497
ms.openlocfilehash: bf8293c6a6cf12154b02979de08035807991052c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376051"
---
# <a name="public-c"></a>public (C++)

## <a name="syntax"></a>Sintaxis

```
public:
   [member-list]
public base-class
```

## <a name="remarks"></a>Observaciones

Cuando precede a una lista de miembros de clase, la palabra clave **public** especifica que esos miembros son accesibles desde cualquier función. Esto se aplica a todos los miembros declarados hasta el especificador de acceso siguiente o el final de la clase.

Cuando precede el nombre de una clase base, la palabra clave **public** especifica que los miembros public y protected de la clase base son miembros públicos y protegidos, respectivamente, de la clase derivada.

El acceso predeterminado de miembros de una clase es privado. El acceso predeterminado de miembros de una estructura o unión es público.

El acceso predeterminado de una clase base es privado para las clases y público para las estructuras. Las uniones no pueden tener clases base.

Para obtener más información, vea [private](../cpp/private-cpp.md), [protected](../cpp/protected-cpp.md), [friend](../cpp/friend-cpp.md)y la tabla de acceso de miembro en Control del acceso a [los miembros](member-access-control-cpp.md)de clase .

## <a name="clr-specific"></a>Específicos de /clr

En los tipos CLR, las palabras clave del especificador de acceso C++**(public**, **private**y **protected)** pueden afectar a la visibilidad de tipos y métodos con respecto a los ensamblados. Para obtener más información, consulte Control de [acceso de miembros](member-access-control-cpp.md).

> [!NOTE]
> Los archivos compilados con [/LN](../build/reference/ln-create-msil-module.md) no se ven afectados por este comportamiento. En este caso, todas las clases administradas (ya sean públicas o privadas) estarán visibles.

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
