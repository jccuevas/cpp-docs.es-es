---
title: __func__
ms.date: 10/19/2017
f1_keywords:
- __func__
ms.assetid: a5299b8d-f0ee-4af2-91dd-8fb165e68798
ms.openlocfilehash: eecd3efea6239c92a8bc81c0ed13a9563e5b87d2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154300"
---
# <a name="func"></a>__func__

**(C ++ 11)**  El identificador predefinido &#95; &#95;func&#95; &#95; se definió implícitamente como una cadena que contiene el nombre no completo y sin adornar de la función envolvente. &#95;&#95;Func&#95; &#95; está asignada por el estándar de C++ y no es una extensión de Microsoft.

## <a name="syntax"></a>Sintaxis

```cpp
__func__
```

## <a name="return-value"></a>Valor devuelto

Devuelve terminada en null const char matriz de caracteres que contiene el nombre de función.

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