---
title: Compilador advertencia (nivel 3) C4839 | Documentos de Microsoft
ms.date: 10/25/2017
ms.technology:
- cpp-tools
ms.topic: error-reference
f1_keywords:
- C4839
dev_langs:
- C++
helpviewer_keywords:
- C4839
ms.assetid: f4f99066-9258-4330-81a8-f4a75a1d95ee
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aee1e564ffd72b9b08d883c94311c2bca72b5aef
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4839"></a>Compilador advertencia (nivel 4) C4839

> uso no estándar de la clase*tipo*' como argumento a una función variádica

En Visual Studio de 2017, clases o structs que se pasan a una variádicas a la función como `printf` debe copiar de forma trivial. Al pasar objetos de este tipo, el compilador simplemente realiza una copia bit a bit y no llama al constructor ni al destructor.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4839:

```cpp
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

    struct S {
        S(int i) : i(i) {}
        S(const S& other) : i(other.i) {}
        operator int() { return i; }
    private:
        int i;
    } s(0);
    printf("%i\n", s); // warning C4840 : non-portable use of class 'main::S'
                      // as an argument to a variadic function
}
```

Para corregir el error, puede llamar a una función miembro que devuelva un tipo que se pueda copiar trivialmente

```cpp
    std::atomic<int> i(0);
    printf("%i\n", i.load());
```

o bien realizar una conversión estática para convertir el objeto antes de pasarlo:

```cpp
    struct S {/* as before */} s(0);
    printf("%i\n", static_cast<int>(s))
```

Para las cadenas creadas y administradas mediante `CStringW`, proporcionado `operator LPCWSTR()` se debe utilizar para convertir un `CStringW` objeto con el puntero de C esperado por la cadena de formato.

```cpp
    CStringW str1;
    CStringW str2;
    // ...
    str1.Format("%s", static_cast<LPCWSTR>(str2));
```