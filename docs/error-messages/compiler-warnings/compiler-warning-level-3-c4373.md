---
title: Advertencia del compilador (nivel 3) C4373
ms.date: 11/04/2016
f1_keywords:
- C4373
helpviewer_keywords:
- C4373
ms.assetid: 670c0ba3-b7d6-4aed-b207-1cb84da3bcde
ms.openlocfilehash: 031b32a03d93a51f6fa00041a5b0bdf99e6eacf1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456061"
---
# <a name="compiler-warning-level-3-c4373"></a>Advertencia del compilador (nivel 3) C4373

> '*función*': la invalidación de funciones virtuales*función_base*', las versiones anteriores del compilador no se reemplazaron cuando los parámetros solo se diferenciaban en los calificadores const y volatile

## <a name="remarks"></a>Comentarios

La aplicación contiene un método en una clase derivada que reemplaza un método virtual en una clase base, y los parámetros en el método de reemplazo difieren solo en un calificador [const](../../cpp/const-cpp.md) o [volatile](../../cpp/volatile-cpp.md) de los parámetros del método virtual. Esto significa que el compilador debe enlazar una referencia a función con el método en la clase derivada o base.

Versiones del compilador anteriores a Visual Studio 2008 enlazan la función con el método de la clase base, a continuación, emiten un mensaje de advertencia. Las versiones posteriores del compilador omiten el `const` o `volatile` calificador, enlazan la función con el método en la clase derivada y después emiten la advertencia **C4373**. Este último comportamiento cumple con el estándar de C++.

## <a name="example"></a>Ejemplo

El siguiente código de ejemplo genera la advertencia C4373. Para resolver este problema, puede hacer la invalidación de usar el mismo calificador CV como la función miembro base, o si no tenía intención de crear una invalidación, puede conceder a la función de la clase derivada un nombre diferente.

```cpp
// c4373.cpp
// compile with: /c /W3
#include <stdio.h>
struct Base
{
    virtual void f(int i) {
        printf("base\n");
    }
};

struct Derived : Base
{
    void f(const int i) {  // C4373
        printf("derived\n");
    }
};

void main()
{
    Derived d;
    Base* p = &d;
    p->f(1);
}
```

```Output
derived
```