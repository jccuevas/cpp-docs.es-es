---
title: ADVERTENCIA del compilador (nivel 3) C4839
ms.date: 09/13/2018
f1_keywords:
- C4839
helpviewer_keywords:
- C4839
ms.assetid: f4f99066-9258-4330-81a8-f4a75a1d95ee
ms.openlocfilehash: 2c238dc16359583bf55f7590d2ce7c0363d66df7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198580"
---
# <a name="compiler-warning-level-3-c4839"></a>ADVERTENCIA del compilador (nivel 3) C4839

> uso no estándar de la clase '*Type*' como argumento de una función variádicas

Las clases o Structs que se pasan a una función variádicas como `printf` se deben poder copiar de forma trivial. Al pasar objetos de este tipo, el compilador simplemente realiza una copia bit a bit y no llama al constructor ni al destructor.

Esta advertencia está disponible a partir de Visual Studio 2017.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4839:

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

En el caso de las cadenas compiladas y administradas mediante `CStringW`, se debe usar el `operator LPCWSTR()` proporcionado para convertir un objeto `CStringW` en el puntero C esperado por la cadena de formato.

```cpp
    CStringW str1;
    CStringW str2;
    // ...
    str1.Format("%s", static_cast<LPCWSTR>(str2));
```
