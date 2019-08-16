---
title: Operadores de &lt;list&gt;
ms.date: 11/04/2016
f1_keywords:
- list/std::operator!=
- list/std::operator&gt;
- list/std::operator&gt;=
- list/std::operator&lt;
- list/std::operator&lt;=
- list/std::operator==
ms.assetid: 8103d8f2-c30f-49ad-ac50-b3ba6a907ebe
helpviewer_keywords:
- std::operator!= (list)
- std::operator&gt; (list)
- std::operator&gt;= (list)
- std::operator&lt; (list)
- std::operator&lt;= (list)
- std::operator== (list)
ms.openlocfilehash: 7b0b7540c1b9a55140405a55e8e034f9c6ec646c
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246463"
---
# <a name="ltlistgt-operators"></a>Operadores de &lt;list&gt;

## <a name="op_neq"></a> operador! =

Comprueba si el objeto de lista del lado izquierdo del operador no es igual que el objeto de lista del lado derecho.

```cpp
bool operator!=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto de tipo `list`.

*Correcto*\
Objeto de tipo `list`.

### <a name="return-value"></a>Valor devuelto

**True** si las listas no son iguales; **False** si son iguales.

### <a name="remarks"></a>Comentarios

La comparación entre los objetos de lista se basa en una comparación en pares de sus elementos. Dos listas son iguales si tienen el mismo número de elementos y sus elementos respectivos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.

### <a name="example"></a>Ejemplo

```cpp
// list_op_ne.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
using namespace std;
list <int> c1, c2;
c1.push_back( 1 );
c2.push_back( 2 );

if ( c1 != c2 )
cout << "Lists not equal." << endl;
else
cout << "Lists equal." << endl;
}
/* Output:
Lists not equal.
*/
```

## <a name="op_lt"></a> operator&lt;

Comprueba si el objeto de lista del lado izquierdo del operador es menor que el objeto de lista del lado derecho.

```cpp
bool operator<(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto de tipo `list`.

*Correcto*\
Objeto de tipo `list`.

### <a name="return-value"></a>Valor devuelto

**True** si la lista del lado izquierdo del operador es menor pero no igual que la lista del lado derecho del operador. En caso contrario, **False**.

### <a name="remarks"></a>Comentarios

La comparación entre los objetos de lista se basa en una comparación en pares de sus elementos. La relación de menor que entre dos objetos se basa en una comparación del primer par de elementos diferentes.

### <a name="example"></a>Ejemplo

```cpp
// list_op_lt.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1, c2;
   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 4 );

   c2.push_back( 1 );
   c2.push_back( 3 );

   if ( c1 < c2 )
      cout << "List c1 is less than list c2." << endl;
   else
      cout << "List c1 is not less than list c2." << endl;
}
/* Output:
List c1 is less than list c2.
*/
```

## <a name="op_lt_eq"></a> Operador&lt;=

Comprueba si el objeto de lista del lado izquierdo del operador es menor o igual que el objeto de lista del lado derecho.

```cpp
bool operator<=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto de tipo `list`.

*Correcto*\
Objeto de tipo `list`.

### <a name="return-value"></a>Valor devuelto

**True** si la lista del lado izquierdo del operador es menor o igual que la lista del lado derecho del operador. En caso contrario, **False**.

### <a name="remarks"></a>Comentarios

La comparación entre los objetos de lista se basa en una comparación en pares de sus elementos. La relación de menor o igual entre dos objetos se basa en una comparación del primer par de elementos diferentes.

### <a name="example"></a>Ejemplo

```cpp
// list_op_le.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1, c2;
   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 4 );

   c2.push_back( 1 );
   c2.push_back( 3 );

   if ( c1 <= c2 )
      cout << "List c1 is less than or equal to list c2." << endl;
   else
      cout << "List c1 is greater than list c2." << endl;
}
/* Output:
List c1 is less than or equal to list c2.
*/
```

## <a name="op_eq_eq"></a> operador ==

Comprueba si el objeto de lista del lado izquierdo del operador es igual que el objeto de lista del lado derecho.

```cpp
bool operator==(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto de tipo `list`.

*Correcto*\
Objeto de tipo `list`.

### <a name="return-value"></a>Valor devuelto

**True** si la lista del lado izquierdo del operador es igual que la lista del lado derecho del operador. En caso contrario, **False**.

### <a name="remarks"></a>Comentarios

La comparación entre los objetos de lista se basa en una comparación en pares de sus elementos. Dos listas son iguales si tienen el mismo número de elementos y sus elementos respectivos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.

### <a name="example"></a>Ejemplo

```cpp
// list_op_eq.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
int main( )
{
   using namespace std;

   list <int> c1, c2;
   c1.push_back( 1 );
   c2.push_back( 1 );

   if ( c1 == c2 )
      cout << "The lists are equal." << endl;
   else
      cout << "The lists are not equal." << endl;
}
/* Output:
The lists are equal.
*/
```

## <a name="op_gt"></a> operator&gt;

Comprueba si el objeto de lista del lado izquierdo del operador es mayor que el objeto de lista del lado derecho.

```cpp
bool operator>(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto de tipo `list`.

*Correcto*\
Objeto de tipo `list`.

### <a name="return-value"></a>Valor devuelto

**True** si la lista del lado izquierdo del operador es mayor que la lista del lado derecho del operador. En caso contrario, **False**.

### <a name="remarks"></a>Comentarios

La comparación entre los objetos de lista se basa en una comparación en pares de sus elementos. La relación de mayor que entre dos objetos se basa en una comparación del primer par de elementos diferentes.

### <a name="example"></a>Ejemplo

```cpp
// list_op_gt.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
int main( )
{
   using namespace std;
   list <int> c1, c2;
   c1.push_back( 1 );
   c1.push_back( 3 );
   c1.push_back( 1 );

   c2.push_back( 1 );
   c2.push_back( 2 );
   c2.push_back( 2 );

   if ( c1 > c2 )
      cout << "List c1 is greater than list c2." << endl;
   else
      cout << "List c1 is not greater than list c2." << endl;
}
/* Output:
List c1 is greater than list c2.
*/
```

## <a name="op_gt_eq"></a> Operador&gt;=

Comprueba si el objeto de lista del lado izquierdo del operador es mayor o igual que el objeto de lista del lado derecho.

```cpp
bool operator>=(
    const list<Type, Allocator>& left,
    const list<Type, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto de tipo `list`.

*Correcto*\
Objeto de tipo `list`.

### <a name="return-value"></a>Valor devuelto

**True** si la lista del lado izquierdo del operador es mayor o igual que la lista del lado derecho del operador. En caso contrario, **False**.

### <a name="remarks"></a>Comentarios

La comparación entre los objetos de lista se basa en una comparación en pares de sus elementos. La relación de mayor o igual entre dos objetos se basa en una comparación del primer par de elementos diferentes.

### <a name="example"></a>Ejemplo

```cpp
// list_op_ge.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1, c2;
   c1.push_back( 1 );
   c1.push_back( 3 );
   c1.push_back( 1 );

   c2.push_back( 1 );
   c2.push_back( 2 );
   c2.push_back( 2 );

   if ( c1 >= c2 )
      cout << "List c1 is greater than or equal to list c2." << endl;
   else
      cout << "List c1 is less than list c2." << endl;
}
/* Output:
List c1 is greater than or equal to list c2.
*/
```
