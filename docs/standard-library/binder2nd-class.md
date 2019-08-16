---
title: binder2nd (Clase)
ms.date: 02/21/2019
f1_keywords:
- functional/std::binder2nd
helpviewer_keywords:
- binder2nd class
ms.assetid: b2a9c1d1-dfc4-4ca9-a10e-ae84e195a62d
ms.openlocfilehash: 5f59887e6c9d2965a6c8680f17a40c5bd93869c0
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243350"
---
# <a name="binder2nd-class"></a>binder2nd (Clase)

Clase de plantilla que proporciona un constructor que convierte un objeto de función binaria en un objeto de función unaria enlazando el segundo argumento de la función binaria a un valor especificado. En desuso en C ++ 11, se ha quitado en C ++ 17.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Operation>
class binder2nd
    : public unaryFunction <typename Operation::first_argument_type,
    typename Operation::result_type>
{
    typedef typename Operation::argument_type argument_type;
    typedef typename Operation::result_type result_type;
    binder2nd(
        const Operation& Func,
        const typename Operation::second_argument_type& right);

    result_type operator()(const argument_type& left) const;
    result_type operator()(argument_type& left) const;
};
```

### <a name="parameters"></a>Parámetros

*Func*\
El objeto de función binaria que se va a convertir en un objeto de función unaria.

*Correcto*\
El valor al que se enlazará el segundo argumento del objeto de función binaria.

*Izquierda*\
El valor del argumento que el objeto binario adaptado compara con el valor fijo del segundo argumento.

## <a name="return-value"></a>Valor devuelto

El objeto de función unaria resultante de enlazar el segundo argumento del objeto de función binaria con el valor *derecho*.

## <a name="remarks"></a>Comentarios

La clase de plantilla almacena una copia de un objeto de función binaria _ *Func* en `op`y una copia de *derecho* en `value`. Define su función miembro `operator()` que devuelva **op**(`left`, **valor**).

Si `Func` es un objeto de tipo `Operation` y c es una constante, a continuación, [bind2nd](../standard-library/functional-functions.md#bind2nd) (`Func`, `c`) es equivalente a la `binder2nd` constructor de clase `binder2nd` \<  **Operación**> (`Func`, `c`) y más conveniente.

## <a name="example"></a>Ejemplo

```cpp
// functional_binder2nd.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

int main()
{
    vector<int> v1;
    vector<int>::iterator Iter;

    int i;
    for (i = 0; i <= 5; i++)
    {
        v1.push_back(5 * i);
    }

    cout << "The vector v1 = ( ";
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    // Count the number of integers > 10 in the vector
    vector<int>::iterator::difference_type result1;
    result1 = count_if(v1.begin(), v1.end(),
        binder2nd<greater<int> >(greater<int>(), 10));
    cout << "The number of elements in v1 greater than 10 is: "
         << result1 << "." << endl;

    // Compare using binder1st fixing 1st argument:
    // count the number of integers < 10 in the vector
    vector<int>::iterator::difference_type result2;
    result2 = count_if(v1.begin(), v1.end(),
        binder1st<greater<int> >(greater<int>(), 10));
    cout << "The number of elements in v1 less than 10 is: "
         << result2 << "." << endl;
}
```

```Output
The vector v1 = ( 0 5 10 15 20 25 )
The number of elements in v1 greater than 10 is: 3.
The number of elements in v1 less than 10 is: 2.
```
