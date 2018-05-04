---
title: __Func__ | Documentos de Microsoft
ms.custom: ''
ms.date: 10/19/2017
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __func__
dev_langs:
- C++
ms.assetid: a5299b8d-f0ee-4af2-91dd-8fb165e68798
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3d78a249fe5b111c17c29895edcdc3fa5ba2f27a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="func"></a>__Func__

**(C ++ 11)**  El identificador predefinido &#95; &#95;func&#95; &#95; se define implícitamente como una cadena que contiene el nombre completo y sin adornar de la función de inclusión. &#95;&#95;Func&#95; &#95; está asignada por el estándar de C++ y no es una extensión de Microsoft.

## <a name="syntax"></a>Sintaxis

```cpp
__func__
```

## <a name="return-value"></a>Valor devuelto

Devuelve un terminada en null const char una matriz de caracteres que contiene el nombre de función.

## <a name="example"></a>Ejemplo

```cpp
#include <string>
#include <iostream>

namespace Test
{
    struct Foo
    {
        static void DoSomething(int i, std::string s)
        {
           std::cout << __func__ << std::endl; // Output: DoSomething
        }
    };
}

int main()
{
    Test::Foo::DoSomething(42, "Hello");

    return 0;
}
```

## <a name="requirements"></a>Requisitos

C++11