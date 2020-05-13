---
title: Advertencia del compilador (nivel 1) C4436
ms.date: 11/04/2016
f1_keywords:
- C4436
helpviewer_keywords:
- C4436
ms.assetid: 2b54a1fc-c9c6-4cc9-90be-faa44fc715d5
ms.openlocfilehash: 7772d835e398ade24b452f2b816afeae09659bf7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162392"
---
# <a name="compiler-warning-level-1-c4436"></a>Advertencia del compilador (nivel 1) C4436

dynamic_cast de la base virtual ' Class1 ' a ' clase2 ' en el constructor o destructor podría producir un error con la compilación de objetos parcialmente construida con/VD2 o definir ' clase2 ' con #pragma vtordisp (2) en vigor

El compilador ha encontrado una operación de `dynamic_cast` con las siguientes características.

- La conversión proviene de un puntero de clase base a un puntero de clase derivada.

- La clase derivada prácticamente hereda la clase base.

- La clase derivada no tiene un campo de `vtordisp` para la base virtual.

- La conversión se encuentra en un constructor o destructor de la clase derivada, o alguna clase que hereda de la clase derivada.

La advertencia indica que el `dynamic_cast` podría no funcionar correctamente, si está funcionando en un objeto construido parcialmente.  Esto sucede si el constructor o destructor derivado está funcionando en un subobjeto de algún otro objeto derivado.  Si la clase derivada denominada en la ADVERTENCIA Nunca se deriva aún más, se puede pasar por alto la advertencia.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4436 y se muestra el problema de generación de código que se produce a partir del campo de `vtordisp` que falta.

```cpp
// C4436.cpp
// To see the warning and runtime assert, compile with: /W1
// To eliminate the warning and assert, compile with: /W1 /vd2
//       or compile with: /W1 /DFIX
#include <cassert>

struct A
{
public:
    virtual ~A() {}
};

#if defined(FIX)
#pragma vtordisp(push, 2)
#endif
struct B : virtual A
{
    B()
    {
        A* a = static_cast<A*>(this);
        B* b = dynamic_cast<B*>(a);     // C4436
        assert(this == b);              // assert unless compiled with /vd2
    }
};
#if defined(FIX)
#pragma vtordisp(pop)
#endif

struct C : B
{
    int i;
};

int main()
{
    C c;
}
```

## <a name="see-also"></a>Consulte también

[dynamic_cast (Operador)](../../cpp/dynamic-cast-operator.md)<br/>
[vtordisp](../../preprocessor/vtordisp.md)<br/>
[Advertencia del compilador (nivel 4) C4437](../../error-messages/compiler-warnings/compiler-warning-level-4-c4437.md)
