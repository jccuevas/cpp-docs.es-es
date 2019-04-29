---
title: expresiones lambda de constexpr en C++
ms.date: 04/08/2019
helpviewer_keywords:
- lambda expressions [C++], constexpr
ms.assetid: b56346cd-fbff-475f-aeaa-ed2010c6d6f7
ms.openlocfilehash: d1bc60a6da813e54c857da38b0164f544216be00
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62368700"
---
# <a name="constexpr-lambda-expressions-in-c"></a>expresiones lambda de constexpr en C++

**Visual Studio 2017 versión 15.3 y versiones posterior** (disponible con [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)): Una expresión lambda se puede declarar como **constexpr** o se usan en una expresión constante cuando se permite la inicialización de cada miembro de datos que captura o se introduce dentro de una expresión constante.

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

[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)<br/>
[Objetos de función en la biblioteca estándar de C++](../standard-library/function-objects-in-the-stl.md)<br/>
[Llamada a función](../cpp/function-call-cpp.md)<br/>
[for_each](../standard-library/algorithm-functions.md#for_each)