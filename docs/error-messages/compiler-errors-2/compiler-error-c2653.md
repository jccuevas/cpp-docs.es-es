---
title: C2653 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/30/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2653
dev_langs:
- C++
helpviewer_keywords:
- C2653
ms.assetid: 3f49e731-affd-43a0-a8d0-181db7650bc3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3f18e3d6210c5d9b9aba4fdfaab296a01d32b6d5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2653"></a>C2653 de Error del compilador

> '*identificador*': no es un nombre de clase o espacio de nombres

La sintaxis del lenguaje requiere una clase, estructura, unión o nombre del espacio de nombres.

Este error puede producirse cuando se usa un nombre que no se ha declarado como una clase, estructura, unión o espacio de nombres delante de un operador de ámbito. Para corregir este problema, declare el nombre o incluir el encabezado que declara el nombre antes de usarlo.

También es posible si se intenta definir C2653 una *espacio de nombres compuesto*, un espacio de nombres que contiene uno o más nombres de espacio de nombres anidado de ámbito. Compuesta espacio de nombres no se permiten definiciones en C++ antes de C ++ 17. Se admiten los espacios de nombres compuestas a partir de Visual Studio 2015 Update 3 cuando se especifica la [/std:c ++ más reciente](../../build/reference/std-specify-language-standard-version.md) opción del compilador. A partir de Visual C++ 2017 versión 15,5, el compilador admite las definiciones de espacio de nombres compuestos cuando el [/std:c ++ 17](../../build/reference/std-specify-language-standard-version.md) se especifica la opción.

## <a name="examples"></a>Ejemplos

Este ejemplo genera C2653 porque se usa pero no declara un nombre de ámbito. El compilador espera que una clase, estructura, unión o nombre de espacio de nombres antes de un operador de ámbito (::).

```cpp
// C2653.cpp
// compile with: /c
class yy {
   void func1(int i);
};

void xx::func1(int m) {}   // C2653, xx is not declared
void yy::func1(int m) {}   // OK
```

En el código que no se compila para C ++ 17 o estándares más adelante, espacios de nombres anidados deben utilizar una declaración de espacio de nombres explícito en cada nivel de anidamiento:

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
