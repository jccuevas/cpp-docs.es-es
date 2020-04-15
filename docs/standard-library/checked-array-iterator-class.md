---
title: checked_array_iterator (Clase)
ms.date: 03/27/2019
f1_keywords:
- iterator/checked_array_iterator
- iterator/stdext::checked_array_iterator::difference_type
- iterator/stdext::checked_array_iterator::pointer
- iterator/stdext::checked_array_iterator::reference
- iterator/stdext::checked_array_iterator::base
helpviewer_keywords:
- stdext::checked_array_iterator [C++], difference_type
- stdext::checked_array_iterator [C++], pointer
- stdext::checked_array_iterator [C++], reference
- stdext::checked_array_iterator [C++], base
ms.assetid: 7f07185e-d588-4ae3-9c4f-84ec4aa25a28
ms.openlocfilehash: f177a45e700ab15852cd9c6d947873d247cf3828
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363871"
---
# <a name="checked_array_iterator-class"></a>checked_array_iterator (Clase)

La clase `checked_array_iterator` permite transformar una matriz o un puntero en un iterador comprobado. Use esta clase como contenedor (mediante la función [make_checked_array_iterator](../standard-library/iterator-functions.md#make_checked_array_iterator)) para matrices o punteros sin formato como una manera dirigida de comprobar y administrar advertencias de puntero no comprobadas en lugar de silenciar de manera global estas advertencias. Si es necesario, puede usar la versión no comprobada de esta clase, [unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md).

> [!NOTE]
> Esta clase es una extensión de Microsoft de la Biblioteca estándar de C++. El código implementado mediante esta función no es portable a los entornos de compilación estándar de C++ que no admiten esta extensión de Microsoft. Para obtener un ejemplo en el que se muestra cómo escribir código que no requiere el uso de esta clase, vea el segundo ejemplo siguiente.

## <a name="syntax"></a>Sintaxis

```cpp
template <class _Iterator>
class checked_array_iterator;
```

## <a name="remarks"></a>Observaciones

Esta clase se define en el espacio de nombres [stdext](../standard-library/stdext-namespace.md).

Para obtener más información y código de ejemplo sobre la característica de iterador comprobado, vea [Iteradores comprobados](../standard-library/checked-iterators.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo definir y utilizar un iterador de matrices comprobado.

Si el destino no es suficientemente grande para contener todos los elementos que se van a copiar, como ocurriría si cambió la línea:

```cpp
copy(a, a + 5, checked_array_iterator<int*>(b, 5));
```

to

```cpp
copy(a, a + 5, checked_array_iterator<int*>(b, 4));
```

Se producirá un error en tiempo de ejecución.

```cpp
// compile with: /EHsc /W4 /MTd
#include <algorithm>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[]={0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b, 5));

   cout << "(";
   for (int i = 0 ; i < 5 ; i++)
      cout << " " << b[i];
   cout << " )" << endl;

   // constructor example
   checked_array_iterator<int*> checked_out_iter(b, 5);
   copy(a, a + 5, checked_out_iter);

   cout << "(";
   for (int i = 0 ; i < 5 ; i++)
      cout << " " << b[i];
   cout << " )" << endl;
}
/* Output:
( 0 1 2 3 4 )
( 0 1 2 3 4 )
*/
```

## <a name="example"></a>Ejemplo

Para evitar la necesidad de la clase `checked_array_iterator` cuando se usan algoritmos de la biblioteca estándar de C++, considere la posibilidad de usar `vector` en lugar de una matriz asignada de forma dinámica. En el ejemplo siguiente se muestra cómo hacerlo:

```cpp
// compile with: /EHsc /W4 /MTd

#include <algorithm>
#include <iostream>
#include <vector>

using namespace std;

int main()
{
    std::vector<int> v(10);
    int *arr = new int[10];
    for (int i = 0; i < 10; ++i)
    {
        v[i] = i;
        arr[i] = i;
    }

    // std::copy(v.begin(), v.end(), arr); will result in
    // warning C4996. To avoid this warning while using int *,
    // use the Microsoft extension checked_array_iterator.
    std::copy(v.begin(), v.end(),
              stdext::checked_array_iterator<int *>(arr, 10));

    // Instead of using stdext::checked_array_iterator and int *,
    // consider using std::vector to encapsulate the array. This will
    // result in no warnings, and the code will be portable.
    std::vector<int> arr2(10);    // Similar to int *arr = new int[10];
    std::copy(v.begin(), v.end(), arr2.begin());

    for (int j = 0; j < arr2.size(); ++j)
    {
        cout << " " << arr2[j];
    }
    cout << endl;

    return 0;
}
/* Output:
0 1 2 3 4 5 6 7 8 9
*/
```

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[checked_array_iterator](#checked_array_iterator)|Construye un `checked_array_iterator` predeterminado o un `checked_array_iterator` a partir de un iterador subyacente.|

### <a name="typedefs"></a>Typedefs

|Nombre del tipo|Descripción|
|-|-|
|[difference_type](#difference_type)|Tipo que proporciona la diferencia entre dos `checked_array_iterator` que hacen referencia a elementos del mismo contenedor.|
|[puntero](#pointer)|Tipo que proporciona un puntero a un elemento direccionado por `checked_array_iterator`.|
|[Referencia](#reference)|Tipo que proporciona una referencia a un elemento direccionado por `checked_array_iterator`.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[base](#base)|Recupera el iterador subyacente de su `checked_array_iterator`.|

### <a name="operators"></a>Operadores

|Operator|Descripción|
|-|-|
|[operadora](#op_eq_eq)|Comprueba dos `checked_array_iterator` para ver si son iguales.|
|[¡Operador!](#op_neq)|Comprueba dos `checked_array_iterator` para ver si son distintos.|
|[operador<](#op_lt)|Comprueba si el `checked_array_iterator` a la izquierda del operador es menor que el `checked_array_iterator` de la derecha.|
|[operador>](#op_gt)|Comprueba si el `checked_array_iterator` a la izquierda del operador es mayor que el `checked_array_iterator` de la derecha.|
|[<de operadores ?](#op_lt_eq)|Comprueba si el `checked_array_iterator` a la izquierda del operador es menor o igual que el `checked_array_iterator` de la derecha.|
|[>de operadores ?](#op_gt_eq)|Comprueba si el `checked_array_iterator` a la izquierda del operador es mayor o igual que el `checked_array_iterator` de la derecha.|
|[operador*](#op_star)|Devuelve el elemento que direcciona un `checked_array_iterator`.|
|[>operador](#op_arrow)|Devuelve un puntero al elemento direccionado por `checked_array_iterator`.|
|[operador++](#op_add_add)|Incrementa el `checked_array_iterator` al elemento siguiente.|
|[operador--](#operator--)|Disminuye el `checked_array_iterator` al elemento anterior.|
|[operador +o](#op_add_eq)|Agrega un desplazamiento especificado a un `checked_array_iterator`.|
|[operador+](#op_add)|Agrega un desplazamiento a un iterador y devuelve el nuevo `checked_array_iterator` que direcciona el elemento insertado en la nueva posición de desplazamiento.|
|[operador-](#operator-_eq)|Disminuye un desplazamiento especificado de un `checked_array_iterator`.|
|[operador-](#operator-)|Disminuye un desplazamiento de un iterador y devuelve el nuevo `checked_array_iterator` que direcciona el elemento insertado en la nueva posición de desplazamiento.|
|[operator&#91;&#93;](#op_at)|Devuelve una referencia a un desplazamiento de elemento con respecto al elemento direccionado por `checked_array_iterator` un número especificado de posiciones.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<iterator>

**Espacio de nombres:** stdext

## <a name="checked_array_iteratorbase"></a><a name="base"></a>checked_array_iterator::base

Recupera el iterador subyacente de su `checked_array_iterator`.

```cpp
_Iterator base() const;
```

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).

### <a name="example"></a>Ejemplo

```cpp
// checked_array_iterators_base.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main() {
   using namespace std;

   int V1[10];

   for (int i = 0; i < 10 ; i++)
      V1[i] = i;

   int* bpos;

   stdext::checked_array_iterator<int*> rpos(V1, 10);
   rpos++;

   bpos = rpos.base ( );
   cout << "The iterator underlying rpos is bpos & it points to: "
        << *bpos << "." << endl;
}
/* Output:
The iterator underlying rpos is bpos & it points to: 1.
*/
```

## <a name="checked_array_iteratorchecked_array_iterator"></a><a name="checked_array_iterator"></a>checked_array_iterator::checked_array_iterator

Construye un `checked_array_iterator` predeterminado o un `checked_array _iterator` a partir de un iterador subyacente.

```cpp
checked_array_iterator();

checked_array_iterator(
    ITerator ptr,
    size_t size,
    size_t index = 0);
```

### <a name="parameters"></a>Parámetros

*Ptr*\
Un puntero a la matriz.

*Tamaño*\
Se refiere al tamaño de la matriz.

*Índice*\
(Opcional) Un elemento de la matriz para inicializar el iterador.  De manera predeterminada, el iterador se inicializa en el primer elemento de la matriz.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).

### <a name="example"></a>Ejemplo

```cpp
// checked_array_iterators_ctor.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   for (int i = 0 ; i < 5 ; i++)
      cout << b[i] << " ";
   cout << endl;

   checked_array_iterator<int*> checked_output_iterator(b,5);
   copy (a, a + 5, checked_output_iterator);
   for (int i = 0 ; i < 5 ; i++)
      cout << b[i] << " ";
   cout << endl;

   checked_array_iterator<int*> checked_output_iterator2(b,5,3);
   cout << *checked_output_iterator2 << endl;
}
/* Output:
0 1 2 3 4
0 1 2 3 4
3
*/
```

## <a name="checked_array_iteratordifference_type"></a><a name="difference_type"></a>checked_array_iterator::difference_type

Tipo que proporciona la diferencia entre dos `checked_array_iterator` que hacen referencia a elementos del mismo contenedor.

```cpp
typedef typename iterator_traits<_Iterator>::difference_type difference_type;
```

### <a name="remarks"></a>Observaciones

El tipo de diferencia `checked_array_iterator` es el mismo que el tipo de diferencia del iterador.

Consulte [checked_array_iterator::operator[]](#op_at) para obtener un ejemplo de código.

Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).

## <a name="checked_array_iteratoroperator"></a><a name="op_eq_eq"></a>checked_array_iterator::operador

Comprueba dos `checked_array_iterator` para ver si son iguales.

```cpp
bool operator==(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parámetros

*Correcto*\
El `checked_array_iterator` con el que se va a comprobar la igualdad.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).

### <a name="example"></a>Ejemplo

```cpp
// checked_array_iterators_opeq.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);
   checked_array_iterator<int*> checked_output_iterator2(b,5);

   if (checked_output_iterator2 == checked_output_iterator)
      cout << "checked_array_iterators are equal" << endl;
   else
      cout << "checked_array_iterators are not equal" << endl;

   copy (a, a + 5, checked_output_iterator);
   checked_output_iterator++;

   if (checked_output_iterator2 == checked_output_iterator)
      cout << "checked_array_iterators are equal" << endl;
   else
      cout << "checked_array_iterators are not equal" << endl;
}
/* Output:
checked_array_iterators are equal
checked_array_iterators are not equal
*/
```

## <a name="checked_array_iteratoroperator"></a><a name="op_neq"></a>checked_array_iterator::operador!

Comprueba dos `checked_array_iterator` para ver si son distintos.

```cpp
bool operator!=(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parámetros

*Correcto*\
El `checked_array_iterator` con el que se va a comprobar la desigualdad.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).

### <a name="example"></a>Ejemplo

```cpp
// checked_array_iterators_opneq.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);
   checked_array_iterator<int*> checked_output_iterator2(b,5);

   if (checked_output_iterator2 != checked_output_iterator)
      cout << "checked_array_iterators are not equal" << endl;
   else
      cout << "checked_array_iterators are equal" << endl;

   copy (a, a + 5, checked_output_iterator);
   checked_output_iterator++;

   if (checked_output_iterator2 != checked_output_iterator)
      cout << "checked_array_iterators are not equal" << endl;
   else
      cout << "checked_array_iterators are equal" << endl;
}
/* Output:
checked_array_iterators are equal
checked_array_iterators are not equal
*/
```

## <a name="checked_array_iteratoroperatorlt"></a><a name="op_lt"></a>checked_array_iterator::operador&lt;

Comprueba si el `checked_array_iterator` a la izquierda del operador es menor que el `checked_array_iterator` de la derecha.

```cpp
bool operator<(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parámetros

*Correcto*\
El `checked_array_iterator` con el que se va a comprobar la desigualdad.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).

### <a name="example"></a>Ejemplo

```cpp
// checked_array_iterators_oplt.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);
   checked_array_iterator<int*> checked_output_iterator2(b,5);

   if (checked_output_iterator2 < checked_output_iterator)
      cout << "checked_output_iterator2 is less than checked_output_iterator" << endl;
   else
      cout << "checked_output_iterator2 is not less than checked_output_iterator" << endl;

   copy (a, a + 5, checked_output_iterator);
   checked_output_iterator++;

   if (checked_output_iterator2 < checked_output_iterator)
      cout << "checked_output_iterator2 is less than checked_output_iterator" << endl;
   else
      cout << "checked_output_iterator2 is not less than checked_output_iterator" << endl;
}
/* Output:
checked_output_iterator2 is not less than checked_output_iterator
checked_output_iterator2 is less than checked_output_iterator
*/
```

## <a name="checked_array_iteratoroperatorgt"></a><a name="op_gt"></a>checked_array_iterator::operador&gt;

Comprueba si el `checked_array_iterator` a la izquierda del operador es mayor que el `checked_array_iterator` de la derecha.

```cpp
bool operator>(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parámetros

*Correcto*\
El `checked_array_iterator` con el que se va a comparar.

### <a name="remarks"></a>Observaciones

Consulte [checked_array_iterator::operator&lt; ](#op_lt) para obtener un ejemplo de código.

Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).

## <a name="checked_array_iteratoroperatorlt"></a><a name="op_lt_eq"></a>checked_array_iterator::operador&lt;=

Comprueba si el `checked_array_iterator` a la izquierda del operador es menor o igual que el `checked_array_iterator` de la derecha.

```cpp
bool operator<=(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parámetros

*Correcto*\
El `checked_array_iterator` con el que se va a comparar.

### <a name="remarks"></a>Observaciones

Consulte [checked_array_iterator::operator&gt; ](#op_gt_eq) para obtener un ejemplo de código.

Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).

## <a name="checked_array_iteratoroperatorgt"></a><a name="op_gt_eq"></a>checked_array_iterator::operador&gt;=

Comprueba si el `checked_array_iterator` a la izquierda del operador es mayor o igual que el `checked_array_iterator` de la derecha.

```cpp
bool operator>=(const checked_array_iterator<_Iterator>& right) const;
```

### <a name="parameters"></a>Parámetros

*Correcto*\
El `checked_array_iterator` con el que se va a comparar.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).

### <a name="example"></a>Ejemplo

```cpp
// checked_array_iterators_opgteq.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);
   checked_array_iterator<int*> checked_output_iterator2(b,5);

   if (checked_output_iterator2 >= checked_output_iterator)
      cout << "checked_output_iterator2 is greater than or equal to checked_output_iterator" << endl;
   else
      cout << "checked_output_iterator2 is less than checked_output_iterator" << endl;

   copy (a, a + 5, checked_output_iterator);
   checked_output_iterator++;

   if (checked_output_iterator2 >= checked_output_iterator)
      cout << "checked_output_iterator2 is greater than or equal to checked_output_iterator" << endl;
   else
      cout << "checked_output_iterator2 is less than checked_output_iterator" << endl;
}
/* Output:
checked_output_iterator2 is greater than or equal to checked_output_iterator
checked_output_iterator2 is less than checked_output_iterator
*/
```

## <a name="checked_array_iteratoroperator"></a><a name="op_star"></a>checked_array_iterator::operador*

Devuelve el elemento que direcciona un `checked_array_iterator`.

```cpp
reference operator*() const;
```

### <a name="return-value"></a>Valor devuelto

El valor del elemento al que se dirige el `checked_array_iterator`.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).

### <a name="example"></a>Ejemplo

```cpp
// checked_array_iterator_pointer.cpp
// compile with: /EHsc
#include <iterator>
#include <algorithm>
#include <vector>
#include <utility>
#include <iostream>

using namespace std;
using namespace stdext;

int main() {
   int a[] = {0, 1, 2, 3, 4};
   int b[5];
   pair<int, int> c[1];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   for (int i = 0 ; i < 5 ; i++)
      cout << b[i] << endl;

    c[0].first = 10;
    c[0].second = 20;

   checked_array_iterator<int*> checked_output_iterator(b,5);
   checked_array_iterator<int*>::pointer p = &(*checked_output_iterator);
   checked_array_iterator<pair<int, int>*> chk_c(c, 1);
   checked_array_iterator<pair<int, int>*>::pointer p_c = &(*chk_c);

   cout << "b[0] = " << *p << endl;
   cout << "c[0].first = " << p_c->first << endl;
}
/* Output:
0
1
2
3
4
b[0] = 0
c[0].first = 10
*/
```

## <a name="checked_array_iteratoroperator-gt"></a><a name="op_arrow"></a>checked_array_iterator::operador-&gt;

Devuelve un puntero al elemento direccionado por `checked_array_iterator`.

```cpp
pointer operator->() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero al elemento al que se dirige el `checked_array_iterator`.

### <a name="remarks"></a>Observaciones

Vea [checked_array_iterator::pointer](#pointer) para obtener un ejemplo de código.

Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).

## <a name="checked_array_iteratoroperator"></a><a name="op_add_add"></a>checked_array_iterator::operador++

Incrementa el `checked_array_iterator` al elemento siguiente.

```cpp
checked_array_iterator& operator++();

checked_array_iterator<_Iterator> operator++(int);
```

### <a name="return-value"></a>Valor devuelto

El primer operador devuelve el `checked_array_iterator` preincrementado y el segundo, el operador de postincremento, devuelve una copia del `checked_array_iterator` incrementado.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).

### <a name="example"></a>Ejemplo

```cpp
// checked_array_iterators_op_plus_plus.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace stdext;
   using namespace std;
   int a[] = {6, 3, 77, 199, 222};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);

   cout << *checked_output_iterator << endl;
   ++checked_output_iterator;
   cout << *checked_output_iterator << endl;
   checked_output_iterator++;
   cout << *checked_output_iterator << endl;
}
/* Output:
6
3
77
*/
```

## <a name="checked_array_iteratoroperator--"></a><a name="operator--"></a>checked_array_iterator::operador--

Disminuye el `checked_array_iterator` al elemento anterior.

```cpp
checked_array_iterator<_Iterator>& operator--();

checked_array_iterator<_Iterator> operator--(int);
```

### <a name="return-value"></a>Valor devuelto

El primer operador devuelve el `checked_array_iterator` prereducido y el segundo, el operador de posdecremento, devuelve una copia del `checked_array_iterator` reducido.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).

### <a name="example"></a>Ejemplo

```cpp
// checked_array_iterators_op_minus_minus.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace stdext;
   using namespace std;
   int a[] = {6, 3, 77, 199, 222};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);

   cout << *checked_output_iterator << endl;
   checked_output_iterator++;
   cout << *checked_output_iterator << endl;
   checked_output_iterator--;
   cout << *checked_output_iterator << endl;
}
/* Output:
6
3
6
*/
```

## <a name="checked_array_iteratoroperator"></a><a name="op_add_eq"></a>checked_array_iterator::operador+o

Agrega un desplazamiento especificado a un `checked_array_iterator`.

```cpp
checked_array_iterator<_Iterator>& operator+=(difference_type _Off);
```

### <a name="parameters"></a>Parámetros

*_Off*\
El desplazamiento en el que se incrementa el iterador.

### <a name="return-value"></a>Valor devuelto

Una referencia al elemento al que se dirige el `checked_array_iterator`.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).

### <a name="example"></a>Ejemplo

```cpp
// checked_array_iterators_op_plus_eq.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace stdext;
   using namespace std;
   int a[] = {6, 3, 77, 199, 222};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);

   cout << *checked_output_iterator << endl;
   checked_output_iterator += 3;
   cout << *checked_output_iterator << endl;
}
/* Output:
6
199
*/
```

## <a name="checked_array_iteratoroperator"></a><a name="op_add"></a>checked_array_iterator::operador+

Agrega un desplazamiento a un iterador y devuelve el nuevo `checked_array_iterator` que direcciona el elemento insertado en la nueva posición de desplazamiento.

```cpp
checked_array_iterator<_Iterator> operator+(difference_type _Off) const;
```

### <a name="parameters"></a>Parámetros

*_Off*\
El desplazamiento que se va a agregar a `checked_array_iterator`.

### <a name="return-value"></a>Valor devuelto

Un `checked_array_iterator` que se dirige al elemento de desplazamiento.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).

### <a name="example"></a>Ejemplo

```cpp
// checked_array_iterators_op_plus.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace stdext;
   using namespace std;
   int a[] = {6, 3, 77, 199, 222};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);

   cout << *checked_output_iterator << endl;
   checked_output_iterator = checked_output_iterator + 3;
   cout << *checked_output_iterator << endl;
}
/* Output:
6
199
*/
```

## <a name="checked_array_iteratoroperator-"></a><a name="operator-_eq"></a>checked_array_iterator::operador-o

Disminuye un desplazamiento especificado de un `checked_array_iterator`.

```cpp
checked_array_iterator<_Iterator>& operator-=(difference_type _Off);
```

### <a name="parameters"></a>Parámetros

*_Off*\
El desplazamiento en el que se incrementa el iterador.

### <a name="return-value"></a>Valor devuelto

Una referencia al elemento al que se dirige el `checked_array_iterator`.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).

### <a name="example"></a>Ejemplo

```cpp
// checked_array_iterators_op_minus_eq.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace stdext;
   using namespace std;
   int a[] = {6, 3, 77, 199, 222};
   int b[5];
   copy(a, a + 5, checked_array_iterator<int*>(b,5));

   checked_array_iterator<int*> checked_output_iterator(b,5);

   checked_output_iterator += 3;
   cout << *checked_output_iterator << endl;
   checked_output_iterator -= 2;
   cout << *checked_output_iterator << endl;
}
/* Output:
199
3
*/
```

## <a name="checked_array_iteratoroperator-"></a><a name="operator-"></a>checked_array_iterator::operador-

Disminuye un desplazamiento de un iterador y devuelve el nuevo `checked_array_iterator` que direcciona el elemento insertado en la nueva posición de desplazamiento.

```cpp
checked_array_iterator<_Iterator> operator-(difference_type _Off) const;

difference_type operator-(const checked_array_iterator& right) const;
```

### <a name="parameters"></a>Parámetros

*_Off*\
El desplazamiento que se restará del `checked_array_iterator`.

### <a name="return-value"></a>Valor devuelto

Un `checked_array_iterator` que se dirige al elemento de desplazamiento.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).

## <a name="checked_array_iteratoroperator"></a><a name="op_at"></a>checked_array_iterator::operador[]

Devuelve una referencia a un desplazamiento de elemento con respecto al elemento direccionado por `checked_array_iterator` un número especificado de posiciones.

```cpp
reference operator[](difference_type _Off) const;
```

### <a name="parameters"></a>Parámetros

*_Off*\
El desplazamiento desde la dirección del `checked_array_iterator`.

### <a name="return-value"></a>Valor devuelto

La referencia al desplazamiento del elemento.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).

### <a name="example"></a>Ejemplo

```cpp
// checked_array_iterators_op_diff.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace std;
   int V1[10];

   for (int i = 0; i < 10 ; i++)
      V1[i] = i;

   // Declare a difference type for a parameter
   stdext::checked_array_iterator<int*>::difference_type diff = 2;

   stdext::checked_array_iterator<int*> VChkIter(V1, 10);

   stdext::checked_array_iterator<int*>::reference refrpos = VChkIter [diff];

   cout << refrpos + 1 << endl;
}
/* Output:
3
*/
```

## <a name="checked_array_iteratorpointer"></a><a name="pointer"></a>checked_array_iterator::pointer

Tipo que proporciona un puntero a un elemento direccionado por `checked_array_iterator`.

```cpp
typedef typename iterator_traits<_Iterator>::pointer pointer;
```

### <a name="remarks"></a>Observaciones

Consulte [checked_array_iterator::operator*](#op_star) para obtener un ejemplo de código.

Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).

## <a name="checked_array_iteratorreference"></a><a name="reference"></a>checked_array_iterator::referencia

Tipo que proporciona una referencia a un elemento direccionado por `checked_array_iterator`.

```cpp
typedef typename iterator_traits<_Iterator>::reference reference;
```

### <a name="remarks"></a>Observaciones

Consulte [checked_array_iterator::operator[]](#op_at) para obtener un ejemplo de código.

Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).

## <a name="see-also"></a>Consulte también

[\<iterador>](../standard-library/iterator.md)\
[Referencia de la biblioteca estándar C++](../standard-library/cpp-standard-library-reference.md)
