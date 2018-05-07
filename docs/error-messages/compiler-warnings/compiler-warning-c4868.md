---
title: C4868 de advertencia del compilador | Documentos de Microsoft
ms.date: 10/26/2017
ms.topic: error-reference
f1_keywords:
- C4868
ms.assetid: fc6aa7e5-34dd-4ec2-88bd-16e430361dc7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 922a1a8434da8449758b9d55ebe89ace2f262cd5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4868"></a>Compilador advertencia (nivel 4) C4868

> '_archivo_(*line_number*)' compilador no puede aplicar el orden de evaluación de izquierda a derecha en la lista de inicializadores entre llaves

Son los elementos de una lista de inicializadores entre llaves se evalúan en orden de izquierda a derecha. Hay dos casos en que el compilador no puede garantizar este orden: el primero es cuando algunos de los elementos son objetos que se pasan por valor; el segundo es cuando se compila con `/clr` y algunos de los elementos son campos de objetos o elementos de la matriz. Cuando el compilador no puede garantizar la evaluación de izquierda a derecha emite la advertencia C4868.

Esta advertencia se puede generar como resultado del trabajo de conformidad del compilador efectuado para Visual C++ 2015 Update 2. Código que se compiló antes de Visual C++ 2015 Update 2 ahora puede generar C4868.

De forma predeterminada, esta advertencia está desactivada. Use `/Wall` para activar esta advertencia.

Para resolver esta advertencia, considere si la evaluación de izquierda a derecha de los elementos de la lista de inicializadores es necesaria, por ejemplo, cuando la evaluación de los elementos puede producir efectos secundarios de dependa del orden. En muchos casos, el orden en que se evalúan los elementos no tiene un efecto observable.

Si el orden de evaluación debe ser de izquierda a derecha, tenga en cuenta si es posible pasar los elementos por `const` referencia en su lugar. Un cambio como este elimina la advertencia en el ejemplo de código siguiente.

## <a name="example"></a>Ejemplo

Este ejemplo genera C4868 y muestra una forma de corregirlo:

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