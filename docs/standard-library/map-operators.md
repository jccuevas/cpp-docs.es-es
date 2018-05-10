---
title: Operadores de &lt;map&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- map/std::operator!=
- map/std::operator&gt;
- map/std::operator&gt;=
- map/std::operator&lt;
- map/std::operator&lt;=
- map/std::operator==
dev_langs:
- C++
ms.assetid: 7df02b9f-701c-44ed-834a-a819badc5bd0
helpviewer_keywords:
- std::operator!= (map)
- std::operator&gt; (map)
- std::operator&gt;= (map)
- std::operator&lt; (map)
- std::operator&lt;= (map)
- std::operator== (map)
ms.openlocfilehash: 60813074eb112836295a72b1c11a24a8c9800313
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="ltmapgt-operators"></a>Operadores de &lt;map&gt;

||||
|-|-|-|
|[operator!=](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|
|[operator&lt;](#op_lt)|[operator&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|
|[operator!= (multimap)](#op_neq_multimap)|[operator&gt;](#op_gt_multimap)|[operator&gt;=](#op_gt_eq_multimap)|
|[operator&lt;](#op_lt_multimap)|[operator&lt;=](#op_lt_eq_multimap)|[operator==](#op_eq_eq_multimap)|

## <a name="op_neq"></a> operator!=

Comprueba si el objeto de mapa del lado izquierdo del operador no es igual que el objeto de mapa del lado derecho.

```cpp
bool operator!=(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

`left` Un objeto de tipo **mapa**.

`right` Un objeto de tipo **mapa**.

### <a name="return-value"></a>Valor devuelto

**True** si los mapas no son iguales; **False** si los mapas son iguales.

### <a name="remarks"></a>Comentarios

La comparación entre los objetos de mapa se basa en una comparación en pares de sus elementos. Dos mapas listas son iguales si tienen el mismo número de elementos y sus elementos respectivos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.

### <a name="example"></a>Ejemplo

```cpp
// map_op_ne.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1, m2, m3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 != m2 )
      cout << "The maps m1 and m2 are not equal." << endl;
   else
      cout << "The maps m1 and m2 are equal." << endl;

   if ( m1 != m3 )
      cout << "The maps m1 and m3 are not equal." << endl;
   else
      cout << "The maps m1 and m3 are equal." << endl;
}
\* Output:
The maps m1 and m2 are not equal.
The maps m1 and m3 are equal.
*\
```

## <a name="op_lt"></a> operator&lt;

Comprueba si el objeto de mapa del lado izquierdo del operador es menor que el objeto de mapa del lado derecho.

```cpp
bool operator<(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

`left` Un objeto de tipo **mapa**.

`right` Un objeto de tipo **mapa**.

### <a name="return-value"></a>Valor devuelto

**True** si el mapa del lado izquierdo del operador es estrictamente menor que el mapa del lado derecho del operador. En caso contrario, **False**.

### <a name="remarks"></a>Comentarios

La comparación entre los objetos de mapa se basa en una comparación en pares de sus elementos. La relación de menor que entre dos objetos se basa en una comparación del primer par de elementos diferentes.

### <a name="example"></a>Ejemplo

```cpp
// map_op_lt.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map<int, int> m1, m2, m3;
   int i;
   typedef pair<int, int> Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
   }

   if ( m1 < m2 )
      cout << "The map m1 is less than the map m2." << endl;
   else
      cout << "The map m1 is not less than the map m2." << endl;

   if ( m1 < m3 )
      cout << "The map m1 is less than the map m3." << endl;
   else
      cout << "The map m1 is not less than the map m3." << endl;
}
\* Output:
The map m1 is less than the map m2.
The map m1 is not less than the map m3.
*\
```

## <a name="op_lt_eq"></a> operator&lt;=

Comprueba si el objeto de mapa del lado izquierdo del operador es menor o igual que el objeto de mapa del lado derecho.

```cpp
bool operator<=(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

`left` Un objeto de tipo **mapa**.

`right` Un objeto de tipo **mapa**.

### <a name="return-value"></a>Valor devuelto

**True** si el mapa del lado izquierdo del operador es menor o igual que el mapa del lado derecho del operador. En caso contrario, **False**.

### <a name="example"></a>Ejemplo

```cpp
// map_op_le.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1, m2, m3, m4;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
      m4.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 <= m2 )
      cout << "The map m1 is less than or equal to the map m2." << endl;
   else
      cout << "The map m1 is greater than the map m2." << endl;

   if ( m1 <= m3 )
      cout << "The map m1 is less than or equal to the map m3." << endl;
   else
      cout << "The map m1 is greater than the map m3." << endl;

   if ( m1 <= m4 )
      cout << "The map m1 is less than or equal to the map m4." << endl;
   else
      cout << "The map m1 is greater than the map m4." << endl;
}
\* Output:
The map m1 is less than or equal to the map m2.
The map m1 is greater than the map m3.
The map m1 is less than or equal to the map m4.
*\
```

## <a name="op_eq_eq"></a>  operator==

Comprueba si el objeto de mapa del lado izquierdo del operador es igual que el objeto de mapa del lado derecho.

```cpp
bool operator==(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

`left` Un objeto de tipo **mapa**.

`right` Un objeto de tipo **mapa**.

### <a name="return-value"></a>Valor devuelto

**True** si el mapa del lado izquierdo del operador es igual que el mapa del lado derecho del operador. En caso contrario, **False**.

### <a name="remarks"></a>Comentarios

La comparación entre los objetos de mapa se basa en una comparación en pares de sus elementos. Dos mapas listas son iguales si tienen el mismo número de elementos y sus elementos respectivos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.

### <a name="example"></a>Ejemplo

```cpp
// map_op_eq.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map < int, int > m1, m2, m3;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 == m2 )
      cout << "The maps m1 and m2 are equal." << endl;
   else
      cout << "The maps m1 and m2 are not equal." << endl;

   if ( m1 == m3 )
      cout << "The maps m1 and m3 are equal." << endl;
   else
      cout << "The maps m1 and m3 are not equal." << endl;
}
\* Output:
The maps m1 and m2 are not equal.
The maps m1 and m3 are equal.
*\
```

## <a name="op_gt"></a> operator&gt;

Comprueba si el objeto de mapa del lado izquierdo del operador es mayor que el objeto de mapa del lado derecho.

```cpp
bool operator>(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

`left` Un objeto de tipo **mapa**.

`right` Un objeto de tipo **mapa**.

### <a name="return-value"></a>Valor devuelto

**True** si el mapa del lado izquierdo del operador es mayor que el mapa del lado derecho del operador. En caso contrario, **False**.

### <a name="remarks"></a>Comentarios

La comparación entre los objetos de mapa se basa en una comparación en pares de sus elementos. La relación de mayor que entre dos objetos se basa en una comparación del primer par de elementos diferentes.

### <a name="example"></a>Ejemplo

```cpp
// map_op_gt.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map < int, int > m1, m2, m3;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
   }

   if ( m1 > m2 )
      cout << "The map m1 is greater than the map m2." << endl;
   else
      cout << "The map m1 is not greater than the map m2." << endl;

   if ( m1 > m3 )
      cout << "The map m1 is greater than the map m3." << endl;
   else
      cout << "The map m1 is not greater than the map m3." << endl;
}
\* Output:
The map m1 is not greater than the map m2.
The map m1 is greater than the map m3.
*\
```

## <a name="op_gt_eq"></a> operator&gt;=

Comprueba si el objeto de mapa del lado izquierdo del operador es mayor o igual que el objeto de mapa del lado derecho.

```cpp
bool operator>=(
      const map <Key, Type, Traits, Allocator>& left,
      const map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

`left` Un objeto de tipo **mapa**.

`right` Un objeto de tipo **mapa**.

### <a name="return-value"></a>Valor devuelto

**True** si el mapa del lado izquierdo del operador es mayor o igual que el mapa del lado derecho de la lista. En caso contrario, **False**.

### <a name="example"></a>Ejemplo

```cpp
// map_op_ge.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map < int, int > m1, m2, m3, m4;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
      m4.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 >= m2 )
      cout << "Map m1 is greater than or equal to map m2." << endl;
   else
      cout << "The map m1 is less than the map m2." << endl;

   if ( m1 >= m3 )
      cout << "Map m1 is greater than or equal to map m3." << endl;
   else
      cout << "The map m1 is less than the map m3." << endl;

   if ( m1 >= m4 )
      cout << "Map m1 is greater than or equal to map m4." << endl;
   else
      cout << "The map m1 is less than the map m4." << endl;
}
\* Output:
The map m1 is less than the map m2.
Map m1 is greater than or equal to map m3.
Map m1 is greater than or equal to map m4.
*\
```

## <a name="op_neq_multimap"></a>  operator!= (multimap)

Comprueba si el objeto de mapa múltiple del lado izquierdo del operador no es igual que el objeto de mapa múltiple del lado derecho.

```cpp
bool operator!=(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

`left` Un objeto de tipo `multimap`.

`right` Un objeto de tipo `multimap`.

### <a name="return-value"></a>Valor devuelto

**True** si los mapas múltiples no son iguales; **False** si los mapas múltiples son iguales.

### <a name="remarks"></a>Comentarios

La comparación entre los objetos de mapa múltiple se basa en una comparación en pares de sus elementos. Dos mapas múltiples son iguales si tienen el mismo número de elementos y sus elementos respectivos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.

### <a name="example"></a>Ejemplo

```cpp
// multimap_op_ne.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1, m2, m3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 != m2 )
      cout << "The multimaps m1 and m2 are not equal." << endl;
   else
      cout << "The multimaps m1 and m2 are equal." << endl;

   if ( m1 != m3 )
      cout << "The multimaps m1 and m3 are not equal." << endl;
   else
      cout << "The multimaps m1 and m3 are equal." << endl;
}
\* Output:
The multimaps m1 and m2 are not equal.
The multimaps m1 and m3 are equal.
*\
```

## <a name="op_lt_multimap"></a> operator&lt;

Comprueba si el objeto de mapa múltiple del lado izquierdo del operador es menor que el objeto de mapa múltiple del lado derecho.

```cpp
bool operator<(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

`left` Un objeto de tipo `multimap`.

`right` Un objeto de tipo `multimap`.

### <a name="return-value"></a>Valor devuelto

**True** si el mapa múltiple del lado izquierdo del operador es estrictamente menor que el mapa múltiple del lado derecho del operador. En caso contrario, **False**.

### <a name="remarks"></a>Comentarios

La comparación entre los objetos de mapa múltiple se basa en una comparación en pares de sus elementos. La relación de menor que entre dos objetos se basa en una comparación del primer par de elementos diferentes.

### <a name="example"></a>Ejemplo

```cpp
// multimap_op_lt.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap < int, int > m1, m2, m3;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
   }

   if ( m1 < m2 )
      cout << "The multimap m1 is less than the multimap m2." << endl;
   else
      cout << "The multimap m1 is not less than the multimap m2." << endl;

   if ( m1 < m3 )
      cout << "The multimap m1 is less than the multimap m3." << endl;
   else
      cout << "The multimap m1 is not less than the multimap m3." << endl;
}
\* Output:
The multimap m1 is less than the multimap m2.
The multimap m1 is not less than the multimap m3.
*\
```

## <a name="eq_multimap"></a> operator&lt;=

Comprueba si el objeto de mapa múltiple del lado izquierdo del operador es menor o igual que el objeto de mapa múltiple del lado derecho.

```cpp
bool operator<=(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

`left` Un objeto de tipo `multimap`.

`right` Un objeto de tipo `multimap`.

### <a name="return-value"></a>Valor devuelto

**True** si el mapa múltiple del lado izquierdo del operador es menor o igual que el mapa múltiple del lado derecho del operador. En caso contrario, **alse**.

### <a name="example"></a>Ejemplo

```cpp
// multimap_op_le.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1, m2, m3, m4;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
      m4.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 <= m2 )
      cout << "m1 is less than or equal to m2" << endl;
   else
      cout << "m1 is greater than m2" << endl;

   if ( m1 <= m3 )
      cout << "m1 is less than or equal to m3" << endl;
   else
      cout << "m1 is greater than m3" << endl;

   if ( m1 <= m4 )
      cout << "m1 is less than or equal to m4" << endl;
   else
      cout << "m1 is greater than m4" << endl;
}
\* Output:
m1 is less than or equal to m2
m1 is greater than m3
m1 is less than or equal to m4
*\
```

## <a name="op_eq_eq_multimap"></a>  operator==

Comprueba si el objeto de mapa múltiple del lado izquierdo del operador es igual que el objeto de mapa múltiple del lado derecho.

```cpp
bool operator==(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

`left` Un objeto de tipo `multimap`.

`right` Un objeto de tipo `multimap`.

### <a name="return-value"></a>Valor devuelto

**rue** si el mapa múltiple del lado izquierdo del operador es igual que el mapa múltiple del lado derecho del operador. En caso contrario, **alse**.

### <a name="remarks"></a>Comentarios

La comparación entre los objetos de mapa múltiple se basa en una comparación en pares de sus elementos. Dos mapas múltiples son iguales si tienen el mismo número de elementos y sus elementos respectivos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.

### <a name="example"></a>Ejemplo

```cpp
// multimap_op_eq.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap<int, int> m1, m2, m3;
   int i;
   typedef pair<int, int> Int_Pair;

   for (i = 0; i < 3; i++)
   {
      m1.insert(Int_Pair(i, i));
      m2.insert(Int_Pair(i, i*i));
      m3.insert(Int_Pair(i, i));
   }

   if ( m1 == m2 )
      cout << "m1 and m2 are equal" << endl;
   else
      cout << "m1 and m2 are not equal" << endl;

   if ( m1 == m3 )
      cout << "m1 and m3 are equal" << endl;
   else
      cout << "m1 and m3 are not equal" << endl;
}
\* Output:
m1 and m2 are not equal
m1 and m3 are equal
*\
```

## <a name="op_gt_multimap"></a> operator&gt;

Comprueba si el objeto de mapa múltiple del lado izquierdo del operador es mayor que el objeto de mapa múltiple del lado derecho.

```cpp
bool operator>(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

`left` Un objeto de tipo `multimap`.

`right` Un objeto de tipo `multimap`.

### <a name="return-value"></a>Valor devuelto

**True** si el mapa múltiple del lado izquierdo del operador es mayor que el mapa múltiple del lado derecho del operador. En caso contrario, **False**.

### <a name="remarks"></a>Comentarios

La comparación entre los objetos de mapa múltiple se basa en una comparación en pares de sus elementos. La relación de mayor que entre dos objetos se basa en una comparación del primer par de elementos diferentes.

### <a name="example"></a>Ejemplo

```cpp
// multimap_op_gt.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap < int, int > m1, m2, m3;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
   }

   if ( m1 > m2 )
      cout << "The multimap m1 is greater than the multimap m2." << endl;
   else
      cout << "Multimap m1 is not greater than multimap m2." << endl;

   if ( m1 > m3 )
      cout << "The multimap m1 is greater than the multimap m3." << endl;
   else
      cout << "The multimap m1 is not greater than the multimap m3." << endl;
}
\* Output:
Multimap m1 is not greater than multimap m2.
The multimap m1 is greater than the multimap m3.
*\
```

## <a name="op_gt_eq_multimap"></a> operator&gt;=

Comprueba si el objeto de mapa múltiple del lado izquierdo del operador es mayor o igual que el objeto de mapa múltiple del lado derecho.

```cpp
bool operator>=(
      const multimap <Key, Type, Traits, Allocator>& left,
      const multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

`left` Un objeto de tipo `multimap`.

`right` Un objeto de tipo `multimap`.

### <a name="return-value"></a>Valor devuelto

**True** si el mapa múltiple del lado izquierdo del operador es mayor o igual que el mapa múltiple del lado derecho de la lista. En caso contrario, **False**.

### <a name="example"></a>Ejemplo

```cpp
// multimap_op_ge.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap < int, int > m1, m2, m3, m4;
   int i;
   typedef pair < int, int > Int_Pair;

   for ( i = 1 ; i < 3 ; i++ )
   {
      m1.insert ( Int_Pair ( i, i ) );
      m2.insert ( Int_Pair ( i, i * i ) );
      m3.insert ( Int_Pair ( i, i - 1 ) );
      m4.insert ( Int_Pair ( i, i ) );
   }

   if ( m1 >= m2 )
      cout << "The multimap m1 is greater than or equal to the multimap m2." << endl;
   else
      cout << "The multimap m1 is less than the multimap m2." << endl;

   if ( m1 >= m3 )
      cout << "The multimap m1 is greater than or equal to the multimap m3." << endl;
   else
      cout << "The multimap m1 is less than the multimap m3." << endl;

   if ( m1 >= m4 )
      cout << "The multimap m1 is greater than or equal to the multimap m4." << endl;
   else
      cout << "The multimap m1 is less than the multimap m4." << endl;
}
\* Output:
The multimap m1 is less than the multimap m2.
The multimap m1 is greater than or equal to the multimap m3.
The multimap m1 is greater than or equal to the multimap m4.
*\
```

## <a name="see-also"></a>Vea también

[\<map>](../standard-library/map.md)<br/>
