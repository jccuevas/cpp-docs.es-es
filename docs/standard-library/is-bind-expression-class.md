---
title: Clase is_bind_expression | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- functional/std::is_bind_expression
dev_langs:
- C++
helpviewer_keywords:
- is_bind_expression class
ms.assetid: 0715f9e9-2239-4778-a1cf-2c21f49dfd47
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 38cf4c4e9e92704e1f6ce635f2a429b4dc9bfcbb
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="isbindexpression-class"></a>is_bind_expression (Clase)

Comprueba si el tipo se genera mediante una llamada a `bind`.

## <a name="syntax"></a>Sintaxis

plantilla<class Ty> struct is_bind_expression () {const bool valor estático;};

## <a name="remarks"></a>Comentarios

El miembro constante `value` es true si el tipo `Ty` es un tipo devuelto mediante una llamada a `bind`. En caso contrario, es false.

## <a name="example"></a>Ejemplo

```cpp
// std__functional__is_bind_expression.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

void square(double x)
{
    std::cout << x << "^2 == " << x * x << std::endl;
}

template<class Expr>
void test_for_bind(const Expr&)
{
    std::cout << std::is_bind_expression<Expr>::value << std::endl;
}

int main()
{
    test_for_bind(3.0 * 3.0);
    test_for_bind(std::bind(square, 3));

    return (0);
}
```

```Output
0
1
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<functional>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[bind](../standard-library/functional-functions.md#bind)<br/>
