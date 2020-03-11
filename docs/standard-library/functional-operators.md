---
title: '&lt;functional&gt; (Operadores)'
ms.date: 11/04/2016
f1_keywords:
- functional/std::operator!=
- functional/std::operator==
helpviewer_keywords:
- functional operators
ms.assetid: d4b3c760-f3e2-4b65-bdaa-d42e8dd6f5e1
ms.openlocfilehash: b396e5c692129821c0deb9aef9469a5c54e600b0
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78876353"
---
# <a name="ltfunctionalgt-operators"></a>&lt;functional&gt; (Operadores)

## <a name="op_eq_eq"></a>operador = =

Comprueba si el objeto al que se puede llamar está vacío.

```cpp
template <class Fty>
    bool operator==(const function<Fty>& f, null_ptr_type npc);

template <class Fty>
    bool operator==(null_ptr_type npc, const function<Fty>& f);
```

### <a name="parameters"></a>Parámetros

\ *fty*
Tipo de función que se va a contener.

\ *f*
Objeto de función

\ *NPC*
Un puntero nulo.

### <a name="remarks"></a>Observaciones

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

## <a name="op_neq"></a>operador! =

Comprueba si el objeto al que se puede llamar no está vacío.

```cpp
template <class Fty>
    bool operator!=(const function<Fty>& f, null_ptr_type npc);

template <class Fty>
    bool operator!=(null_ptr_type npc, const function<Fty>& f);
```

### <a name="parameters"></a>Parámetros

\ *fty*
Tipo de función que se va a contener.

\ *f*
Objeto de función

\ *NPC*
Un puntero nulo.

### <a name="remarks"></a>Observaciones

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
