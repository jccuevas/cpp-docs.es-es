---
title: '&lt;functional&gt; (Operadores) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- functional/std::operator!=
- functional/std::operator==
dev_langs:
- C++
helpviewer_keywords:
- functional operators
ms.assetid: d4b3c760-f3e2-4b65-bdaa-d42e8dd6f5e1
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 82ae23b5176ae6986447a9a1218e3bac91c0b741
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="ltfunctionalgt-operators"></a>&lt;functional&gt; (Operadores)

|||
|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|

## <a name="op_eq_eq"></a>  operator==

Comprueba si el objeto al que se puede llamar está vacío.

```cpp
template <class Fty>
bool operator==(const function<Fty>& f, null_ptr_type npc);

template <class Fty>
bool operator==(null_ptr_type npc, const function<Fty>& f);
```

### <a name="parameters"></a>Parámetros

`Fty` El tipo de función que va a contener.

`f` El objeto de función

`npc` Un puntero nulo.

### <a name="remarks"></a>Comentarios

Los dos operadores toman un argumento que es una referencia a un objeto `function` y un argumento que es una constante de puntero nulo. Ambos devuelven true únicamente si el objeto `function` está vacío.

### <a name="example"></a>Ejemplo

```cpp
// std__functional__operator_eq.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
{
    return (-val);
}

int main()
{
    std::function<int(int)> fn0;
    std::cout << std::boolalpha << "empty == "
        << (fn0 == 0) << std::endl;

    std::function<int(int)> fn1(neg);
    std::cout << std::boolalpha << "empty == "
        << (fn1 == 0) << std::endl;

    return (0);
}

```

```Output
empty == true
empty == false
```

## <a name="op_neq"></a> operator!=

Comprueba si el objeto al que se puede llamar no está vacío.

```cpp
template <class Fty>
bool operator!=(const function<Fty>& f, null_ptr_type npc);

template <class Fty>
bool operator!=(null_ptr_type npc, const function<Fty>& f);
```

### <a name="parameters"></a>Parámetros

`Fty` El tipo de función que va a contener.

`f` El objeto de función

`npc` Un puntero nulo.

### <a name="remarks"></a>Comentarios

Los dos operadores toman un argumento que es una referencia a un objeto `function` y un argumento que es una constante de puntero nulo. Ambos devuelven True solo si el objeto `function` no está vacío.

### <a name="example"></a>Ejemplo

```cpp
// std__functional__operator_ne.cpp
// compile with: /EHsc
#include <functional>
#include <iostream>

int neg(int val)
    {
    return (-val);
    }

int main()
    {
    std::function<int (int)> fn0;
    std::cout << std::boolalpha << "not empty == "
        << (fn0 != 0) << std::endl;

    std::function<int (int)> fn1(neg);
    std::cout << std::boolalpha << "not empty == "
        << (fn1 != 0) << std::endl;

    return (0);
    }

```

```Output
not empty == false
not empty == true
```

## <a name="see-also"></a>Vea también

[\<functional>](../standard-library/functional.md)<br/>
