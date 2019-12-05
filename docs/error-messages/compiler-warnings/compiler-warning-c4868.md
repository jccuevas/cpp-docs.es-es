---
title: ADVERTENCIA del compilador C4868
ms.date: 10/26/2017
f1_keywords:
- C4868
helpviewer_keywords:
- C4868
ms.assetid: fc6aa7e5-34dd-4ec2-88bd-16e430361dc7
ms.openlocfilehash: c1d49eb61a5c7c47fa83dacb39ed50f42e0fb147
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810484"
---
# <a name="compiler-warning-level-4-c4868"></a>ADVERTENCIA del compilador (nivel 4) C4868

> el compilador '_File_(*line_number*) ' no puede aplicar el orden de evaluación de izquierda a derecha en la lista de inicializadores entre llaves

Los elementos de una lista de inicializadores entre llaves se van a evaluar en orden de izquierda a derecha. Hay dos casos en los que el compilador no puede garantizar este orden: el primero es cuando algunos de los elementos son objetos pasados por valor; la segunda es cuando se compila con `/clr` y algunos de los elementos son campos de objetos o son elementos de matriz. Cuando el compilador no puede garantizar la evaluación de izquierda a derecha, emite una advertencia C4868.

Esta advertencia se puede generar como resultado del trabajo de conformidad del compilador realizado para Visual Studio 2015 Update 2. El código que se compiló antes de Visual Studio 2015 Update 2 ahora puede generar C4868.

De forma predeterminada, esta advertencia está desactivada. Use `/Wall` para activar esta advertencia.

Para resolver esta advertencia, primero debe considerar si es necesario la evaluación de izquierda a derecha de los elementos de la lista de inicializadores, por ejemplo, cuando la evaluación de los elementos puede producir efectos secundarios dependientes del orden. En muchos casos, el orden en el que se evalúan los elementos no tiene un efecto observable.

Si el orden de evaluación debe ser de izquierda a derecha, considere la posibilidad de pasar los elementos por `const` referencia en su lugar. Un cambio como este elimina la advertencia en el ejemplo de código siguiente.

## <a name="example"></a>Ejemplo

En este ejemplo se genera C4868 y se muestra una manera de corregirlo:

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