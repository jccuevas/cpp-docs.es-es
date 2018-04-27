---
title: '&lt;deque&gt; (Operadores) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- deque/std::operator!=
- deque/std::operator&gt;
- deque/std::operator&gt;=
- deque/std::operator&lt;
- deque/std::operator&lt;=
- deque/std::operator==
dev_langs:
- C++
ms.assetid: 482d7c92-54c7-493b-99e6-2a73617481a5
caps.latest.revision: 7
manager: ghogen
helpviewer_keywords:
- std::operator!= (deque)
- std::operator&gt; (deque)
- std::operator&gt;= (deque)
- std::operator&lt; (deque)
- std::operator&lt;= (deque)
- std::operator== (deque)
ms.openlocfilehash: 4cc8784c30615a9cb580aa27c072a035c7ec4951
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="ltdequegt-operators"></a>&lt;deque&gt; (Operadores)

||||
|-|-|-|
|[operator!=](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|
|[operator&lt;](#op_lt)|[operator&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a> operator!=

Comprueba si el objeto deque a la izquierda del operador no es igual que el objeto deque del lado derecho.

```cpp
bool operator!=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

`left` Un objeto de tipo `deque`.

`right` Un objeto de tipo `deque`.

### <a name="return-value"></a>Valor devuelto

**True** si los objetos deque no son iguales; **False** si son iguales.

### <a name="remarks"></a>Comentarios

La comparación entre los objetos deque se basa en una comparación en pares de sus elementos. Dos objetos deque son iguales si tienen el mismo número de elementos y sus elementos respectivos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.

### <a name="example"></a>Ejemplo

```cpp
// deque_op_ne.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c2.push_back( 2 );

   if ( c1 != c2 )
      cout << "The deques are not equal." << endl;
   else
      cout << "The deques are equal." << endl;
}
\* Output:
The deques are not equal.
*\
```

## <a name="op_lt"></a> operator&lt;

Comprueba si el objeto deque a la izquierda del operador es menor que el objeto deque del lado derecho.

```cpp
bool operator<(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

`left` Un objeto de tipo `deque`.

`right` Un objeto de tipo `deque`.

### <a name="return-value"></a>Valor devuelto

**True** si el deque del lado izquierdo del operador es menor y no igual que el deque del lado derecho del operador. Si no es así, **False**.

### <a name="remarks"></a>Comentarios

La comparación entre los objetos deque se basa en una comparación en pares de sus elementos. La relación de menor que entre dos objetos se basa en una comparación del primer par de elementos diferentes.

### <a name="example"></a>Ejemplo

```cpp
// deque_op_lt.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 4 );

   c2.push_back( 1 );
   c2.push_back( 3 );

   if ( c1 < c2 )
      cout << "Deque c1 is less than deque c2." << endl;
   else
      cout << "Deque c1 is not less than deque c2." << endl;
}
\* Output:
Deque c1 is less than deque c2.
*\
```

## <a name="op_lt_eq"></a> operator&lt;=

Comprueba si el objeto deque a la izquierda del operador es menor o igual que el objeto deque del lado derecho.

```cpp
bool operator<=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

`left` Un objeto de tipo `deque`.

`right` Un objeto de tipo `deque`.

### <a name="return-value"></a>Valor devuelto

**True** si el deque del lado izquierdo del operador es menor o igual que el deque del lado derecho del operador. Si no es así, **False**.

### <a name="remarks"></a>Comentarios

La comparación entre los objetos deque se basa en una comparación en pares de sus elementos. La relación de menor o igual entre dos objetos se basa en una comparación del primer par de elementos diferentes.

### <a name="example"></a>Ejemplo

```cpp
// deque_op_le.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 4 );

   c2.push_back( 1 );
   c2.push_back( 3 );

   if ( c1 <= c2 )
      cout << "Deque c1 is less than or equal to deque c2." << endl;
   else
      cout << "Deque c1 is greater than deque c2." << endl;
}
\* Output:
Deque c1 is less than or equal to deque c2.
*\

```

## <a name="op_eq_eq"></a>  operator==

Comprueba si el objeto deque a la izquierda del operador es igual que el objeto deque del lado derecho.

```cpp
bool operator==(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

`left` Un objeto de tipo `deque`.

`right` Un objeto de tipo `deque`.

### <a name="return-value"></a>Valor devuelto

**True** si el deque del lado izquierdo del operador es igual que el deque del lado derecho del operador. Si no es así, **False**.

### <a name="remarks"></a>Comentarios

La comparación entre los objetos deque se basa en una comparación en pares de sus elementos. Dos deques son iguales si tienen el mismo número de elementos y sus elementos respectivos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.

### <a name="example"></a>Ejemplo

```cpp
// deque_op_eq.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c2.push_back( 1 );

   if ( c1 == c2 )
      cout << "The deques are equal." << endl;
   else
      cout << "The deques are not equal." << endl;

   c1.push_back( 1 );
   if ( c1 == c2 )
      cout << "The deques are equal." << endl;
   else
      cout << "The deques are not equal." << endl;
}
\* Output:
The deques are equal.
The deques are not equal.
*\

```

## <a name="op_gt"></a> operator&gt;

Comprueba si el objeto deque a la izquierda del operador es mayor que el objeto deque del lado derecho.

```cpp
bool operator>(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

`left` Un objeto de tipo `deque`.

`right` Un objeto de tipo `deque`.

### <a name="return-value"></a>Valor devuelto

**True** si el deque del lado izquierdo del operador es mayor que el deque del lado derecho del operador. Si no es así, **False**.

### <a name="remarks"></a>Comentarios

La comparación entre los objetos deque se basa en una comparación en pares de sus elementos. La relación de mayor que entre dos objetos se basa en una comparación del primer par de elementos diferentes.

### <a name="example"></a>Ejemplo

```cpp
// deque_op_gt.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c1.push_back( 3 );
   c1.push_back( 1 );

   c2.push_back( 1 );
   c2.push_back( 2 );
   c2.push_back( 2 );

   if ( c1 > c2 )
      cout << "Deque c1 is greater than deque c2." << endl;
   else
      cout << "Deque c1 is not greater than deque c2." << endl;
}
\* Output:
Deque c1 is greater than deque c2.
*\

```

## <a name="op_gt_eq"></a> operator&gt;=

Comprueba si el objeto deque a la izquierda del operador es mayor o igual que el objeto deque del lado derecho.

```cpp
bool operator>=(const deque<Type, Allocator>& left, const deque<Type, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

`left` Un objeto de tipo `deque`.

`right` Un objeto de tipo `deque`.

### <a name="return-value"></a>Valor devuelto

**True** si el deque del lado izquierdo del operador es mayor o igual que el deque del lado derecho del operador. Si no es así, **False**.

### <a name="remarks"></a>Comentarios

La comparación entre los objetos deque se basa en una comparación en pares de sus elementos. La relación de mayor o igual entre dos objetos se basa en una comparación del primer par de elementos diferentes.

### <a name="example"></a>Ejemplo

```cpp
// deque_op_ge.cpp
// compile with: /EHsc
#include <deque>
#include <iostream>

int main( )
{
   using namespace std;
   deque <int> c1, c2;

   c1.push_back( 1 );
   c1.push_back( 3 );
   c1.push_back( 1 );

   c2.push_back( 1 );
   c2.push_back( 2 );
   c2.push_back( 2 );

   if ( c1 >= c2 )
      cout << "Deque c1 is greater than or equal to deque c2." << endl;
   else
      cout << "Deque c1 is less than deque c2." << endl;
}
\* Output:
Deque c1 is greater than or equal to deque c2.
*\
```

## <a name="see-also"></a>Vea también

[\<deque>](../standard-library/deque.md)<br/>
