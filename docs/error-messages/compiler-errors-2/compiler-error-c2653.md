---
title: Error del compilador C2653
ms.date: 11/30/2017
f1_keywords:
- C2653
helpviewer_keywords:
- C2653
ms.assetid: 3f49e731-affd-43a0-a8d0-181db7650bc3
ms.openlocfilehash: d4a3a8a74483317b87e16458f44016f0aeca1379
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471154"
---
# <a name="compiler-error-c2653"></a>Error del compilador C2653

> '*identificador*': no es un nombre de clase o espacio de nombres

La sintaxis del lenguaje requiere una clase, estructura, unión o nombre del espacio de nombres.

Este error puede producirse cuando se usa un nombre que no se ha declarado como una clase, estructura, unión o espacio de nombres delante de un operador de ámbito. Para corregir este problema, declare el nombre o incluir el encabezado que declara el nombre antes de utilizarse.

También es posible si se intenta definir C2653 un *espacio de nombres compuesto*, un espacio de nombres que contiene uno o más nombres de espacio de nombres con ámbito anidado. Compuesta de espacio de nombres no se permiten definiciones en C++ antes de C ++ 17. Se admiten los espacios de nombres compuestas a partir de Visual Studio 2015 Update 3 cuando se especifica la [/std: c ++ más reciente](../../build/reference/std-specify-language-standard-version.md) opción del compilador. A partir de Visual C++ 2017 versión 15.5, el compilador admite las definiciones de espacio de nombres compuestos cuando el [/std: c ++ 17](../../build/reference/std-specify-language-standard-version.md) se especifica la opción.

## <a name="examples"></a>Ejemplos

Este ejemplo genera C2653 porque se usa pero no declara un nombre de ámbito. El compilador espera una clase, estructura, unión o espacio de nombres antes de un operador de ámbito (::).

```cpp
// C2653.cpp
// compile with: /c
class yy {
   void func1(int i);
};

void xx::func1(int m) {}   // C2653, xx is not declared
void yy::func1(int m) {}   // OK
```

En el código que no se compila para C ++ 17 o posterior estándares, espacios de nombres anidados deben usar una declaración de espacio de nombres explícito en cada nivel de anidamiento:

```cpp
// C2653b.cpp
namespace a::b {int i;}   // C2653 prior to Visual C++ 2015 Update 3,
                          // C2429 thereafter. Use /std:c++17 or /std:c++latest to fix.

namespace a {             // Use this form for compliant code under /std:c++14 (the default)
   namespace b {          // or when using compilers before Visual Studio 2015 update 3.
      int i;
   }
}

int main() {
   a::b::i = 2;
}
```
