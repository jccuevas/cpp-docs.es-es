---
title: Clase is_placeholder | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- functional/std::is_placeholder
dev_langs:
- C++
helpviewer_keywords:
- is_placeholder class
ms.assetid: 2b21a792-96d1-4bb8-b911-0db796510835
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b577803f766d8f5cafa054e84b5b7ec0f152480b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33852245"
---
# <a name="isplaceholder-class"></a>is_placeholder (Clase)

Comprueba si el tipo es un marcador de posición.

## <a name="syntax"></a>Sintaxis

struct is_placeholder () {const int valor estático;};

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
