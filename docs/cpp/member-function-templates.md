---
title: Plantillas de función miembro
ms.date: 11/04/2016
helpviewer_keywords:
- function templates, member functions
ms.assetid: 83d51835-6a27-40ed-997c-7d90dc9182d8
ms.openlocfilehash: 6955d755897d326479d2b3789edb02ff66806175
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460845"
---
# <a name="member-function-templates"></a>Plantillas de función miembro

El término plantilla de miembro se refiere tanto a las plantillas de función miembro como a las plantillas de clase anidada. Las plantillas de función miembro son funciones de plantilla que son miembros de una clase o una plantilla de clase.

Las funciones miembro pueden ser plantillas de función en varios contextos. Todas las funciones de plantillas de clase son genéricas pero no se hace referencia a ellas como plantillas de miembro o plantillas de función miembro. Si estas funciones miembro tienen sus propios argumentos de plantilla, se consideran plantillas de función miembro.

## <a name="example"></a>Ejemplo

Las plantillas de función miembro de clases de plantilla o clases que no son de plantilla se declaran como plantillas de función con sus parámetros de plantilla.

```cpp
// member_function_templates.cpp
struct X
{
   template <class T> void mf(T* t) {}
};

int main()
{
   int i;
   X* x = new X();
   x->mf(&i);
}
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra una plantilla de función miembro de una clase de plantilla.

```cpp
// member_function_templates2.cpp
template<typename T>
class X
{
public:
   template<typename U>
   void mf(const U &u)
   {
   }
};

int main()
{
}
```

## <a name="example"></a>Ejemplo

```cpp
// defining_member_templates_outside_class.cpp
template<typename T>
class X
{
public:
   template<typename U>
   void mf(const U &u);
};

template<typename T> template <typename U>
void X<T>::mf(const U &u)
{
}

int main()
{
}
```

## <a name="example"></a>Ejemplo

No se permite que las clases locales tengan plantillas de miembro.

Las funciones de plantilla de miembro no pueden ser funciones virtuales y no pueden invalidar funciones virtuales de una clase base cuando se declaran con el mismo nombre que una función virtual de clase base.

El ejemplo siguiente muestra una conversión definida por el usuario con plantilla:

```cpp
// templated_user_defined_conversions.cpp
template <class T>
struct S
{
   template <class U> operator S<U>()
   {
      return S<U>();
   }
};

int main()
{
   S<int> s1;
   S<long> s2 = s1;  // Convert s1 using UDC and copy constructs S<long>.
}
```

## <a name="see-also"></a>Vea también

[Plantillas de función](../cpp/function-templates.md)