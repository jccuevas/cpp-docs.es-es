---
title: las expresiones lambda de constexpr en C++ | Microsoft Docs
ms.custom: ''
ms.date: 07/19/2017
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- lambda expressions [C++], constexpr
ms.assetid: b56346cd-fbff-475f-aeaa-ed2010c6d6f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1b4636333861cc853130a777956ca4b88114f3c6
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/28/2018
ms.locfileid: "43131404"
---
# <a name="constexpr-lambda-expressions-in-c"></a>expresiones lambda de constexpr en C++
**Visual Studio 2017 versión 15.3 y versiones posterior** (disponible con [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): una expresión lambda se puede declarar como **constexpr** o usar en una expresión constante cuando la inicialización de cada uno miembro de datos que se captura o presenta está permitida en una expresión constante.  

```cpp
    int y = 32;
    auto answer = [y]() constexpr 
    {
        int x = 10;
        return y + x; 
    };

    constexpr int Increment(int n) 
    {
        return [n] { return n + 1; }();
    }
``` 
Una expresión lambda es implícitamente **constexpr** si su resultado satisface los requisitos de un **constexpr** función:
```cpp
    auto answer = [](int n) 
    {
        return 32 + n; 
    };

    constexpr int response = answer(10);
``` 
Si una expresión lambda es implícita o explícitamente **constexpr**y convertirlo en un puntero de función, la función resultante es también **constexpr**:

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```
  
## <a name="see-also"></a>Vea también  
 [Referencia del lenguaje C++](../cpp/cpp-language-reference.md)   
 [Objetos de función en la biblioteca estándar de C++](../standard-library/function-objects-in-the-stl.md)   
 [Llamada de función](../cpp/function-call-cpp.md)   
 [for_each](../standard-library/algorithm-functions.md#for_each)