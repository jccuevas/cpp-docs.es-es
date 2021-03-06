---
title: binder1st (Clase)
ms.date: 02/21/2019
f1_keywords:
- functional/std::binder1st
helpviewer_keywords:
- binder1st class
ms.assetid: 6b8ee343-c82f-48f8-867d-06f9d1d324c0
ms.openlocfilehash: 15b704134d47b7bf7d8857bf380c756b0b03a1b0
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688386"
---
# <a name="binder1st-class"></a>binder1st (Clase)

Una plantilla de clase que proporciona un constructor que convierte un objeto de función binaria en un objeto de función unaria enlazando el primer argumento de la función binaria a un valor especificado. Quedó en desuso en C++ 11 en favor del [enlace](functional-functions.md#bind)y se quitó en c++ 17.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Operation>
class binder1st
    : public unaryFunction <typename Operation::second_argument_type,
                             typename Operation::result_type>
{
public:
    typedef typename Operation::argument_type argument_type;
    typedef typename Operation::result_type result_type;
    binder1st(
        const Operation& binary_fn,
        const typename Operation::first_argument_type& left);

    result_type operator()(const argument_type& right) const;
    result_type operator()(const argument_type& right) const;

protected:
    Operation op;
    typename Operation::first_argument_type value;
};
```

### <a name="parameters"></a>Parámetros

\ *binary_fn*
El objeto de función binaria que se va a convertir en un objeto de función unaria.

\ *izquierda*
El valor al que se enlazará el primer argumento del objeto de función binaria.

\ *derecha*
El valor del argumento que el objeto binario adaptado compara con el valor fijo del segundo argumento.

## <a name="return-value"></a>Valor devuelto

El objeto de función unaria resultante de enlazar el primer argumento del objeto de función binaria al valor *izquierdo*.

## <a name="remarks"></a>Comentarios

La plantilla de clase almacena una copia de un objeto de función binaria *binary_fn* en `op` y una copia de *izquierda* en `value`. Define su función miembro `operator()` como si devolviera `op(value, right)`.

Si *binary_fn* es un objeto de tipo `Operation` y `c` es una constante, `bind1st(binary_fn, c)` es un equivalente más cómodo de `binder1st<Operation>(binary_fn, c)`. Para obtener más información, vea [bind1st](../standard-library/functional-functions.md#bind1st).

## <a name="example"></a>Ejemplo

```cpp
// functional_binder1st.cpp
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
        binder1st<less<int> >(less<int>(), 10));
    cout << "The number of elements in v1 greater than 10 is: "
         << result1 << "." << endl;

    // Compare use of binder2nd fixing 2nd argument:
    // count the number of integers < 10 in the vector
    vector<int>::iterator::difference_type result2;
    result2 = count_if(v1.begin(), v1.end(),
        binder2nd<less<int> >(less<int>(), 10));
    cout << "The number of elements in v1 less than 10 is: "
         << result2 << "." << endl;
}
```

```Output
The vector v1 = ( 0 5 10 15 20 25 )
The number of elements in v1 greater than 10 is: 3.
The number of elements in v1 less than 10 is: 2.
```
