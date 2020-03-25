---
title: Error del compilador C2248
ms.date: 11/04/2016
f1_keywords:
- C2248
helpviewer_keywords:
- C2248
ms.assetid: 7a3ba0e8-d3b9-4bb9-95db-81ef17e31d23
ms.openlocfilehash: 843676638037aab9544f1fbd8c5c6d56d351e485
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206563"
---
# <a name="compiler-error-c2248"></a>Error del compilador C2248

'*member*': no se puede obtener acceso al miembro '*access_level*' declarado en la clase '*Class*'

Los miembros de una clase derivada no pueden tener acceso a `private` miembros de una clase base. No se puede tener acceso a `private` o `protected` miembros de instancias de clase.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C2248 cuando se tiene acceso a miembros privados o protegidos de una clase desde fuera de la clase. Para corregir este problema, no tenga acceso a estos miembros directamente fuera de la clase. Use datos de miembros públicos y funciones miembro para interactuar con la clase.

```cpp
// C2248_access.cpp
// compile with: cl /EHsc /W4 C2248_access.cpp
#include <stdio.h>

class X {
public:
    int  m_publicMember;
    void setPrivateMember( int i ) {
        m_privateMember = i;
        printf_s("\n%d", m_privateMember);
    }
protected:
    int  m_protectedMember;

private:
    int  m_privateMember;
} x;

int main() {
    x.m_publicMember = 4;
    printf_s("\n%d", x.m_publicMember);
    x.m_protectedMember = 2; // C2248 m_protectedMember is protected
    x.m_privateMember = 3;   // C2248  m_privMemb is private
    x.setPrivateMember(0);   // OK uses public access function
}
```

Otro problema de conformidad que expone C2248 es el uso de los amigos y la especialización de la plantilla. Para corregir este problema, declare funciones de plantilla de confianza mediante una lista de parámetros de plantilla vacía < > o parámetros de plantilla específicos.

```cpp
// C2248_template.cpp
// compile with: cl /EHsc /W4 C2248_template.cpp
template<class T>
void f(T t) {
    t.i;   // C2248
}

struct S {
private:
    int i;

public:
    S() {}
    friend void f(S);   // refer to the non-template function void f(S)
    // To fix, comment out the previous line and
    // uncomment the following line.
    // friend void f<S>(S);
};

int main() {
    S s;
    f<S>(s);
}
```

Otro problema de conformidad que expone C2248 es cuando se intenta declarar un Friend de una clase y cuando la clase no está visible para la Declaración friend en el ámbito de la clase. Para corregir este problema, conceda confianza a la clase envolvente.

```cpp
// C2248_enclose.cpp
// compile with: cl /W4 /c C2248_enclose.cpp
class T {
    class S {
        class E {};
    };
    friend class S::E;   // C2248
};

class A {
    class S {
        class E {};
        friend class A;  // grant friendship to enclosing class
    };
    friend class S::E;   // OK
};
```
