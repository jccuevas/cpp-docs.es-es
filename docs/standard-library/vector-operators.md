---
title: Operadores de &lt;vector&gt;
ms.date: 11/04/2016
f1_keywords:
- vector/std::operator!=
- vector/std::operator&gt;
- vector/std::operator&gt;=
- vector/std::operator&lt;
- vector/std::operator&lt;=
- vector/std::operator==
ms.assetid: 1d14f312-6f59-4ec7-88ae-95f89a558823
helpviewer_keywords:
- std::operator!= (vector)
- std::operator&gt; (vector)
- std::operator&gt;= (vector)
- std::operator&lt; (vector)
- std::operator&lt;= (vector)
- std::operator== (vector)
ms.openlocfilehash: f6717add93c489f536bd0c0b0f82b74bbd915985
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79427576"
---
# <a name="ltvectorgt-operators"></a>Operadores de &lt;vector&gt;

## <a name="op_neq"></a>operador! =

Comprueba si el objeto en el lado izquierdo del operador no es igual al objeto del lado derecho.

```cpp
bool operator!=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
Objeto de tipo `vector`.

\ *derecha*
Objeto de tipo `vector`.

### <a name="return-value"></a>Valor devuelto

**true** si los vectores no son iguales, **false** si los vectores son iguales.

### <a name="remarks"></a>Observaciones

Dos vectores son iguales si tienen el mismo número de elementos y sus elementos respectivos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.

### <a name="example"></a>Ejemplo

```cpp
// vector_op_ne.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2;
   v1.push_back( 1 );
     v2.push_back( 2 );

   if ( v1 != v2 )
      cout << "Vectors not equal." << endl;
   else
      cout << "Vectors equal." << endl;
}
```

```Output
Vectors not equal.
```

## <a name="op_lt"></a> operator&lt;

Comprueba si el objeto en el lado izquierdo del operador es menor que el objeto del lado derecho.

```cpp
bool operator<(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
Objeto de tipo `vector`.

\ *derecha*
Objeto de tipo `vector`.

### <a name="return-value"></a>Valor devuelto

Es **true** si el vector del lado izquierdo del operador es menor que el vector del lado derecho del operador. De lo contrario, es **false**.

### <a name="example"></a>Ejemplo

```cpp
// vector_op_lt.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2;
   v1.push_back( 1 );
   v1.push_back( 2 );
   v1.push_back( 4 );

   v2.push_back( 1 );
   v2.push_back( 3 );

   if ( v1 < v2 )
      cout << "Vector v1 is less than vector v2." << endl;
   else
      cout << "Vector v1 is not less than vector v2." << endl;
}
```

```Output
Vector v1 is less than vector v2.
```

## <a name="op_lt_eq"></a>operador&lt;=

Comprueba si el objeto en el lado izquierdo del operador es menor o igual que el objeto del lado derecho.

```cpp
bool operator<=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
Objeto de tipo `vector`.

\ *derecha*
Objeto de tipo `vector`.

### <a name="return-value"></a>Valor devuelto

Es **true** si el vector del lado izquierdo del operador es menor o igual que el vector del lado derecho del operador. De lo contrario, es **false**.

### <a name="example"></a>Ejemplo

```cpp
// vector_op_le.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2;
   v1.push_back( 1 );
   v1.push_back( 2 );
   v1.push_back( 4 );

   v2.push_back( 1 );
   v2.push_back( 3 );

   if ( v1 <= v2 )
      cout << "Vector v1 is less than or equal to vector v2." << endl;
   else
      cout << "Vector v1 is greater than vector v2." << endl;
}
```

```Output
Vector v1 is less than or equal to vector v2.
```

## <a name="op_eq_eq"></a>operador = =

Comprueba si el objeto en el lado izquierdo del operador es igual al objeto del lado derecho.

```cpp
bool operator==(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
Objeto de tipo `vector`.

\ *derecha*
Objeto de tipo `vector`.

### <a name="return-value"></a>Valor devuelto

Es **true** si el vector del lado izquierdo del operador es igual que el vector del lado derecho del operador. De lo contrario, es **false**.

### <a name="remarks"></a>Observaciones

Dos vectores son iguales si tienen el mismo número de elementos y sus elementos respectivos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.

### <a name="example"></a>Ejemplo

```cpp
// vector_op_eq.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2;
   v1.push_back( 1 );
   v2.push_back( 1 );

   if ( v1 == v2 )
      cout << "Vectors equal." << endl;
   else
      cout << "Vectors not equal." << endl;
}
```

```Output
Vectors equal.
```

## <a name="op_gt"></a> operator&gt;

Comprueba si el objeto en el lado izquierdo del operador es mayor que el objeto del lado derecho.

```cpp
bool operator>(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
Objeto de tipo `vector`.

\ *derecha*
Objeto de tipo `vector`.

### <a name="return-value"></a>Valor devuelto

Es **true** si el vector del lado izquierdo del operador es mayor que el vector del lado derecho del operador. De lo contrario, es **false**.

### <a name="example"></a>Ejemplo

```cpp
// vector_op_gt.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2;
   v1.push_back( 1 );
   v1.push_back( 3 );
   v1.push_back( 1 );

   v2.push_back( 1 );
   v2.push_back( 2 );
   v2.push_back( 2 );

   if ( v1 > v2 )
      cout << "Vector v1 is greater than vector v2." << endl;
   else
      cout << "Vector v1 is not greater than vector v2." << endl;
}
```

```Output
Vector v1 is greater than vector v2.
```

## <a name="op_gt_eq"></a>operador&gt;=

Comprueba si el objeto en el lado izquierdo del operador es mayor o igual que el objeto del lado derecho.

```cpp
bool operator>=(const vector<Type, Allocator>& left, const vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
Objeto de tipo `vector`.

\ *derecha*
Objeto de tipo `vector`.

### <a name="return-value"></a>Valor devuelto

Es **true** si el vector del lado izquierdo del operador es mayor o igual que el vector del lado derecho del operador. De lo contrario, es **false**.

### <a name="example"></a>Ejemplo

```cpp
// vector_op_ge.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2;
   v1.push_back( 1 );
   v1.push_back( 3 );
   v1.push_back( 1 );

     v2.push_back( 1 );
   v2.push_back( 2 );
   v2.push_back( 2 );

   if ( v1 >= v2 )
      cout << "Vector v1 is greater than or equal to vector v2." << endl;
   else
      cout << "Vector v1 is less than vector v2." << endl;
}
```

```Output
Vector v1 is greater than or equal to vector v2.
```
