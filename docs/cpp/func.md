---
title: __func__
ms.date: 10/19/2017
f1_keywords:
- __func__
ms.assetid: a5299b8d-f0ee-4af2-91dd-8fb165e68798
ms.openlocfilehash: 8e94caffe120c325478d8b4f24c1915a516d69f4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179827"
---
# <a name="__func__"></a>__func__

**(C++ 11)** El identificador &#95; &#95;predefinido FUNC&#95; &#95; se define implícitamente como una cadena que contiene el nombre no completo y sin adornar de la función de inclusión. &#95;&#95;FUNC&#95; &#95; se asigna mediante el C++ estándar y no es una extensión de Microsoft.

## <a name="syntax"></a>Sintaxis

```cpp
__func__
```

## <a name="return-value"></a>Valor devuelto

Devuelve una matriz const char terminada en NULL de caracteres que contiene el nombre de la función.

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
