---
title: Advertencia del compilador (nivel 4) C4437
ms.date: 11/04/2016
ms.assetid: dc07e350-20eb-474c-a7ad-f841ae7ec339
ms.openlocfilehash: 29dd5e7aff8a12ab3df2e56c9f7517ca0f80bdbe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50569187"
---
# <a name="compiler-warning-level-4-c4437"></a>Advertencia del compilador (nivel 4) C4437

dynamic_cast de la base virtual 'clase1' a 'clase2' podría producir un error en algunos contextos compilar con/vd2 o defina 'clase2' con #pragma vtordisp (2) en vigor

De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.

El compilador ha encontrado un `dynamic_cast` operación con las siguientes características.

- La conversión es desde un puntero de clase base a un puntero de la clase derivada.

- La clase derivada hereda virtualmente la clase base.

- La clase derivada no tiene un `vtordisp` campo para la base virtual.

- La conversión no se encuentra en un constructor o destructor de la clase derivada, o alguna clase que más se hereda de la clase derivada (en caso contrario, advertencia del compilador se emitirán C4436).

La advertencia indica que el `dynamic_cast` es posible que no funcionen correctamente si se está ejecutando en un objeto parcialmente construido.  Esta situación se produce cuando se llama a la función de inclusión de un constructor o destructor de una clase que hereda la clase derivada que se menciona en la advertencia.  Si la clase derivada que se menciona en la advertencia nunca es más derivadas, o la función de inclusión no se llama durante la construcción de objetos o la destrucción, se puede omitir la advertencia.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4437 y muestra el problema de generación de código que se origina desde el que falta `vtordisp` campo.

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

## <a name="see-also"></a>Vea también

[dynamic_cast (Operador)](../../cpp/dynamic-cast-operator.md)<br/>
[vtordisp](../../preprocessor/vtordisp.md)<br/>
[Advertencia del compilador (nivel 1) C4436](../../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)