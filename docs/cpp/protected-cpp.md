---
title: protected (C++)
ms.date: 11/04/2016
f1_keywords:
- protected_cpp
helpviewer_keywords:
- protected keyword [C++], member access
- protected keyword [C++]
ms.assetid: 863d299f-fc0d-45d5-a1a7-bd24b7778a93
ms.openlocfilehash: 79ca081726c1f26a251763e2533ade730f075e2f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317264"
---
# <a name="protected-c"></a>protected (C++)

## <a name="syntax"></a>Sintaxis

```
protected:
   [member-list]
protected base-class
```

## <a name="remarks"></a>Observaciones

La palabra clave **protected** especifica el acceso a los miembros de la clase en la *lista de miembros* hasta el siguiente especificador de acceso **(público** o **privado)** o al final de la definición de clase. Los miembros de clase declarados como **protegidos** solo pueden utilizarse de la siguiente manera:

- Funciones miembro de la clase que declaró originalmente estos miembros.

- Objetos friend de la clase que declaró originalmente estos miembros.

- Clases derivadas con acceso público o protegido desde la clase que declaró originalmente estos miembros.

- Clases directas derivadas de forma privada que también tienen acceso privado a miembros protegidos.

Cuando precede el nombre de una clase base, la palabra clave **protected** especifica que los miembros públicos y protegidos de la clase base son miembros protegidos de sus clases derivadas.

Los miembros protegidos no son tan privados como los miembros **privados,** a los que solo pueden acceder los miembros de la clase en la que se declaran, pero no son tan públicos como los miembros **públicos,** a los que se puede acceder en cualquier función.

Los miembros protegidos que también se declaran como **estáticos** son accesibles para cualquier función friend o miembro de una clase derivada. Los miembros protegidos que no se declaran como **estáticos** son accesibles para amigos y funciones miembro en una clase derivada solo a través de un puntero a, referencia a u objeto de la clase derivada.

Para obtener información relacionada, vea [friend](../cpp/friend-cpp.md), [public](../cpp/public-cpp.md), [private](../cpp/private-cpp.md)y la tabla de acceso de miembro s en Control del acceso a [los miembros](member-access-control-cpp.md)de clase .

## <a name="clr-specific"></a>Específicos de /clr

En los tipos CLR, las palabras clave del especificador de acceso C++**(public**, **private**y **protected)** pueden afectar a la visibilidad de tipos y métodos con respecto a los ensamblados. Para obtener más información, consulte Control de [acceso de miembros](member-access-control-cpp.md).

> [!NOTE]
> Los archivos compilados con [/LN](../build/reference/ln-create-msil-module.md) no se ven afectados por este comportamiento. En este caso, todas las clases administradas (ya sean públicas o privadas) estarán visibles.

## <a name="end-clr-specific"></a>Específicos de END /clr

## <a name="example"></a>Ejemplo

```cpp
// keyword_protected.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class X {
public:
   void setProtMemb( int i ) { m_protMemb = i; }
   void Display() { cout << m_protMemb << endl; }
protected:
   int  m_protMemb;
   void Protfunc() { cout << "\nAccess allowed\n"; }
} x;

class Y : public X {
public:
   void useProtfunc() { Protfunc(); }
} y;

int main() {
   // x.m_protMemb;         error, m_protMemb is protected
   x.setProtMemb( 0 );   // OK, uses public access function
   x.Display();
   y.setProtMemb( 5 );   // OK, uses public access function
   y.Display();
   // x.Protfunc();         error, Protfunc() is protected
   y.useProtfunc();      // OK, uses public access function
                        // in derived class
}
```

## <a name="see-also"></a>Consulte también

[Controlar el acceso a los miembros de clase](member-access-control-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)
