---
title: is_placeholder (Clase)
ms.date: 11/04/2016
f1_keywords:
- functional/std::is_placeholder
helpviewer_keywords:
- is_placeholder class
ms.assetid: 2b21a792-96d1-4bb8-b911-0db796510835
ms.openlocfilehash: 2c7848c88194a9b541867b26ffe27764ad862503
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613738"
---
# <a name="isplaceholder-class"></a>is_placeholder (Clase)

Comprueba si el tipo es un marcador de posición.

## <a name="syntax"></a>Sintaxis

struct is_placeholder {const int valor estático;};

## <a name="remarks"></a>Comentarios

El valor constante `value` es 0 si el tipo `Ty` no es un marcador de posición. En caso contrario, su valor es la posición del argumento de llamada de función al que enlaza. Se usa para determinar el valor `N` del enésimo marcador de posición `_N`.

## <a name="example"></a>Ejemplo

```cpp
// std__functional__is_placeholder.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

using namespace std::placeholders;

template<class Expr>
void test_for_placeholder(const Expr&)
{
    std::cout << std::is_placeholder<Expr>::value << std::endl;
}

int main()
{
    test_for_placeholder(3.0);
    test_for_placeholder(_3);

    return (0);
}
```

```Output
0
3
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<functional>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[_1 (Objeto)](../standard-library/1-object.md)<br/>
