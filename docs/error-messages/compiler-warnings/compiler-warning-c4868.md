---
title: Advertencia del compilador C4868
ms.date: 10/26/2017
f1_keywords:
- C4868
ms.assetid: fc6aa7e5-34dd-4ec2-88bd-16e430361dc7
ms.openlocfilehash: d0bc8716e53e71c52f6a31036a95d0b4cefedd79
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481322"
---
# <a name="compiler-warning-level-4-c4868"></a>Advertencia (nivel 4) del compilador C4868

> '_archivo_(*line_number*)' compilador no puede aplicar el orden de evaluación de izquierda a derecha en la lista de inicializadores entre llaves

Son los elementos de una lista de inicializadores entre llaves se evalúan en orden de izquierda a derecha. Hay dos casos en que el compilador no puede garantizar este orden: la primera es cuando algunos de los elementos son objetos que se pasan por valor; la segunda es cuando se compila con `/clr` y algunos de los elementos son campos de objetos o elementos de la matriz. Cuando el compilador no puede garantizar la evaluación de izquierda a derecha emite la advertencia C4868.

Esta advertencia puede generarse como resultado del trabajo de conformidad del compilador efectuado para Visual C++ 2015 Update 2. El código compilado antes de Visual C++ 2015 Update 2 ahora puede generar C4868.

De forma predeterminada, esta advertencia está desactivada. Use `/Wall` para activar esta advertencia.

Para resolver esta advertencia, considere en primer lugar si la evaluación de izquierda a derecha de los elementos de lista de inicializadores es necesaria, como cuando la evaluación de los elementos puede producir efectos secundarios depende del orden. En muchos casos, el orden en que se evalúan los elementos no tiene un efecto visible.

Si el orden de evaluación debe ser de izquierda a derecha, considere la posibilidad de si es posible pasar los elementos `const` hacen referencia en su lugar. Un cambio como este elimina la advertencia en el siguiente ejemplo de código.

## <a name="example"></a>Ejemplo

Este ejemplo genera C4868 y muestra cómo corregirlo:

```cpp
// C4868.cpp
// compile with: /c /Wall
#include <cstdio>

class HasCopyConstructor
{
public:
    int x;

    HasCopyConstructor(int x): x(x) {}

    HasCopyConstructor(const HasCopyConstructor& h): x(h.x)
    {
        printf("Constructing %d\n", h.x);
    }
};

class TripWarning4868
{
public:
    // note that taking "HasCopyConstructor" parameters by-value will trigger copy-construction.
    TripWarning4868(HasCopyConstructor a, HasCopyConstructor b) {}

    // This variation will not trigger the warning:
    // TripWarning4868(const HasCopyConstructor& a, const HasCopyConstructor& b) {}
};

int main()
{
    HasCopyConstructor a{1};
    HasCopyConstructor b{2};

    // the warning will indicate the below line, the usage of the braced initializer list.
    TripWarning4868 warningOnThisLine{a, b};
};
```