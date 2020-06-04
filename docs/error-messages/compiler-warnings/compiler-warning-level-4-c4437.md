---
title: Advertencia del compilador (nivel 4) C4437
ms.date: 11/04/2016
f1_keywords:
- C4437
helpviewer_keywords:
- C4437
ms.assetid: dc07e350-20eb-474c-a7ad-f841ae7ec339
ms.openlocfilehash: 84c6e8d09495d871b8c490a92558aaba14b0574c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185339"
---
# <a name="compiler-warning-level-4-c4437"></a>Advertencia del compilador (nivel 4) C4437

no se pudo dynamic_cast de la base virtual ' Class1 ' a ' clase2 ' en algunos contextos compilados con/VD2 o definir ' clase2 ' con #pragma vtordisp (2) en vigor

De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.

El compilador ha encontrado una operación de `dynamic_cast` con las siguientes características.

- La conversión proviene de un puntero de clase base a un puntero de clase derivada.

- La clase derivada prácticamente hereda la clase base.

- La clase derivada no tiene un campo de `vtordisp` para la base virtual.

- No se encuentra la conversión en un constructor o destructor de la clase derivada, o alguna clase que hereda de la clase derivada (de lo contrario, se emitirá la advertencia del compilador C4436).

La advertencia indica que el `dynamic_cast` podría no funcionar correctamente si está funcionando en un objeto construido parcialmente.  Esta situación se produce cuando se llama a la función de inclusión desde un constructor o un destructor de una clase que hereda la clase derivada denominada en la advertencia.  Si la clase derivada que se nombra en la ADVERTENCIA Nunca se deriva más o no se llama a la función de inclusión durante la construcción o destrucción del objeto, se puede omitir la advertencia.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4437 y se muestra el problema de generación de código que se produce a partir del campo de `vtordisp` que falta.

```cpp
// C4437.cpp
// To see the warning and runtime assert, compile with: /W4
// To eliminate the warning and assert, compile with: /W4 /vd2
//       or compile with: /W4 /DFIX
#pragma warning(default : 4437)
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
        func();
    }

    void func()
    {
        A* a = static_cast<A*>(this);
        B* b = dynamic_cast<B*>(a);     // C4437
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
[Advertencia del compilador (nivel 1) C4436](../../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)
