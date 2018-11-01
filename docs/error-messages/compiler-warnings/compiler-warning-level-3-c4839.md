---
title: Compilador advertencia (nivel 3) C4839
ms.date: 09/13/2018
f1_keywords:
- C4839
helpviewer_keywords:
- C4839
ms.assetid: f4f99066-9258-4330-81a8-f4a75a1d95ee
ms.openlocfilehash: 09b6e5b8dc984b35df7de96f5cf8610f2b0f16af
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536649"
---
# <a name="compiler-warning-level-3-c4839"></a>Compilador advertencia (nivel 3) C4839

> uso no estándar de la clase*tipo*' como argumento a una función variádica

Clases o structs que se pasan a una función variádica como `printf` deben poder copiar trivialmente. Al pasar objetos de este tipo, el compilador simplemente realiza una copia bit a bit y no llama al constructor ni al destructor.

Esta advertencia está disponible a partir de Visual Studio 2017.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4839:

```cpp
// C4839.cpp
// compile by using: cl /EHsc /W3 C4839.cpp
#include <atomic>
#include <memory>
#include <stdio.h>

int main()
{
    std::atomic<int> i(0);
    printf("%i\n", i); // error C4839: non-standard use of class 'std::atomic<int>'
                        // as an argument to a variadic function
                        // note: the constructor and destructor will not be called;
                        // a bitwise copy of the class will be passed as the argument
                        // error C2280: 'std::atomic<int>::atomic(const std::atomic<int> &)':
                        // attempting to reference a deleted function
}
```

Para corregir el error, puede llamar a una función miembro que devuelva un tipo que se pueda copiar trivialmente

```cpp
    std::atomic<int> i(0);
    printf("%i\n", i.load());
```

Para las cadenas compiladas y administradas mediante `CStringW`, proporcionado `operator LPCWSTR()` debe usarse para convertir un `CStringW` objeto en el puntero C esperado por la cadena de formato.

```cpp
    CStringW str1;
    CStringW str2;
    // ...
    str1.Format("%s", static_cast<LPCWSTR>(str2));
```