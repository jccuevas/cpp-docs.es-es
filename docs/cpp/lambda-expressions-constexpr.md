---
title: Expresiones Lambda en C++ constexpr | Documentos de Microsoft
ms.custom: 
ms.date: 07/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- lambda expressions [C++], constexpr
ms.assetid: b56346cd-fbff-475f-aeaa-ed2010c6d6f7
caps.latest.revision: 0
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: c6221118477c79d683d468469b1f87dfa33efded
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="constexpr-lambda-expressions-in-c"></a>constexpr expresiones Lambda en C++
**Visual Studio 2017 15,3 y versiones posteriores** (disponible con [/std:c ++ 17](../build/reference/std-specify-language-standard-version.md)): una expresión lambda se puede declarar como `constexpr` o usar en una expresión constante cuando la inicialización de cada miembro de datos que TI captura o presenta se permite dentro de una expresión constante.  

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
Una expresión lambda es implícitamente `constexpr` si su resultado satisface los requisitos de un `constexpr` función:
```cpp
    auto answer = [](int n) 
    {
        return 32 + n; 
    };

    constexpr int response = answer(10);
``` 
Si una expresión lambda es implícita o explícitamente `constexpr`y convertirlo en un puntero a función, la función resultante también es `constexpr`:

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
