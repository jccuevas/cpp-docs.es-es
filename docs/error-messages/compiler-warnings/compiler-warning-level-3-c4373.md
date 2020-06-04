---
title: Advertencia del compilador (nivel 3) C4373
ms.date: 11/04/2016
f1_keywords:
- C4373
helpviewer_keywords:
- C4373
ms.assetid: 670c0ba3-b7d6-4aed-b207-1cb84da3bcde
ms.openlocfilehash: 5891d4679b74695f187fb50bb24fe941882fdcc7
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518353"
---
# <a name="compiler-warning-level-3-c4373"></a>Advertencia del compilador (nivel 3) C4373

> '*función*': la función virtual invalida '*base_function*'; las versiones anteriores del compilador no se reemplazaron cuando los parámetros solo se diferenciaban en los calificadores const o volatile

## <a name="remarks"></a>Notas

La aplicación contiene un método en una clase derivada que reemplaza un método virtual en una clase base, y los parámetros en el método de reemplazo difieren solo en un calificador [const](../../cpp/const-cpp.md) o [volatile](../../cpp/volatile-cpp.md) de los parámetros del método virtual. Esto significa que el compilador debe enlazar una referencia a función con el método en la clase derivada o base.

Las versiones del compilador anteriores a Visual Studio 2008 enlazan la función al método en la clase base y luego emiten un mensaje de advertencia. Las versiones posteriores del compilador omiten el calificador `const` o `volatile`, enlazan la función al método en la clase derivada y después emiten la advertencia **C4373**. Este último comportamiento cumple con el estándar de C++.

## <a name="example"></a>Ejemplo

El siguiente código de ejemplo genera la advertencia C4373. Para resolver este problema, puede hacer que la invalidación use los mismos calificadores CV que la función miembro base, o bien, si no desea crear una invalidación, puede asignar un nombre diferente a la función de la clase derivada.

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

int main()
{
    Derived d;
    Base* p = &d;
    p->f(1);
}
```

```Output
derived
```
