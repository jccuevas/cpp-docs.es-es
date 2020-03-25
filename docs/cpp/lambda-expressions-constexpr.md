---
title: expresiones lambda de constexpr enC++
ms.date: 04/08/2019
helpviewer_keywords:
- lambda expressions [C++], constexpr
ms.assetid: b56346cd-fbff-475f-aeaa-ed2010c6d6f7
ms.openlocfilehash: 9467d9e404204012df6461adacd5dc4cdbdfe71d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179580"
---
# <a name="constexpr-lambda-expressions-in-c"></a>expresiones lambda de constexpr enC++

**Visual Studio 2017 versión 15,3 y posterior** (disponible con [/STD: c++ 17](../build/reference/std-specify-language-standard-version.md)): una expresión lambda se puede declarar como **constexpr** o utilizarse en una expresión constante cuando la inicialización de cada miembro de datos que captura o presenta se permite dentro de una expresión constante.

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

Una expresión lambda es implícitamente **constexpr** si su resultado cumple los requisitos de una función **constexpr** :

```cpp
    auto answer = [](int n)
    {
        return 32 + n;
    };

    constexpr int response = answer(10);
```

Si una expresión lambda es implícita o explícitamente **constexpr**y se convierte en un puntero de función, la función resultante también es **constexpr**:

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```

## <a name="see-also"></a>Consulte también

[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)<br/>
[Objetos de función en la biblioteca estándar de C++](../standard-library/function-objects-in-the-stl.md)<br/>
[Llamada a función](../cpp/function-call-cpp.md)<br/>
[for_each](../standard-library/algorithm-functions.md#for_each)
