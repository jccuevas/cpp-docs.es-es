---
title: Operadores de &lt;hash_set&gt;
ms.date: 03/27/2019
f1_keywords:
- hash_set/std::operator!=
- hash_set/std::operator==
ms.assetid: 403d8e4e-0b3f-43fb-bc5a-8100c4f331c5
ms.openlocfilehash: 5830c9e459c0d778e85c5ab5900d39c3190df178
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368570"
---
# <a name="lthash_setgt-operators"></a>Operadores de &lt;hash_set&gt;

||||
|-|-|-|
|[¡Operador!](#op_neq)|[operator!= (hash_multiset)](#op_neq_hash_multiset)|[operadora](#op_eq_eq)|
|[operador (hash_multiset)](#op_eq_eq_hash_multiset)|

## <a name="operator"></a><a name="op_neq"></a>¡Operador!

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Comprueba si el objeto hash_set del lado izquierdo del operador no es igual que el objeto hash_set del lado derecho.

```cpp
bool operator!=(const hash_set <Key, Traits, Allocator>& left, const hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto de tipo `hash_set`.

*Correcto*\
Objeto de tipo `hash_set`.

### <a name="return-value"></a>Valor devuelto

**true** si los objetos hash_set no son iguales; **false** si los objetos hash_set son iguales.

### <a name="remarks"></a>Observaciones

La comparación entre los objetos hash_set se basa en una comparación en pares de sus elementos. Dos objetos hash_set son iguales si tienen el mismo número de elementos y sus elementos respectivos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.

Los miembros de los archivos de encabezado de>>[hash_map](../standard-library/hash-map.md) y [hash_set<](../standard-library/hash-set.md)<se encuentran en el espacio de nombres [stdext](../standard-library/stdext-namespace.md).

### <a name="example"></a>Ejemplo

```cpp
// hash_set_op_ne.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1, hs2, hs3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hs1.insert ( i );
      hs2.insert ( i * i );
      hs3.insert ( i );
   }

   if ( hs1 != hs2 )
      cout << "The hash_sets hs1 and hs2 are not equal." << endl;
   else
      cout << "The hash_sets hs1 and hs2 are equal." << endl;

   if ( hs1 != hs3 )
      cout << "The hash_sets hs1 and hs3 are not equal." << endl;
   else
      cout << "The hash_sets hs1 and hs3 are equal." << endl;
}
```

```Output
The hash_sets hs1 and hs2 are not equal.
The hash_sets hs1 and hs3 are equal.
```

## <a name="operator"></a><a name="op_eq_eq"></a>operadora

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Comprueba si el objeto hash_set del lado izquierdo del operador es igual que el objeto hash_set del lado derecho.

```cpp
bool operator!==(const hash_set <Key, Traits, Allocator>& left, const hash_set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto de tipo `hash_set`.

*Correcto*\
Objeto de tipo `hash_set`.

### <a name="return-value"></a>Valor devuelto

**True** si el objeto hash_set del lado izquierdo del operador es igual que el objeto hash_set del lado derecho del operador. En caso contrario, **False**.

### <a name="remarks"></a>Observaciones

La comparación entre los objetos hash_set se basa en una comparación en pares de sus elementos. Dos objetos hash_set son iguales si tienen el mismo número de elementos y sus elementos respectivos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.

### <a name="example"></a>Ejemplo

```cpp
// hash_set_op_eq.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 == s2 )
      cout << "The hash_sets s1 and s2 are equal." << endl;
   else
      cout << "The hash_sets s1 and s2 are not equal." << endl;

   if ( s1 == s3 )
      cout << "The hash_sets s1 and s3 are equal." << endl;
   else
      cout << "The hash_sets s1 and s3 are not equal." << endl;
}
```

```Output
The hash_sets s1 and s2 are not equal.
The hash_sets s1 and s3 are equal.
```

## <a name="operator-hash_multiset"></a><a name="op_neq_hash_multiset"></a>operador! (hash_multiset)

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Comprueba si el objeto hash_multiset del lado izquierdo del operador no es igual que el objeto hash_multiset del lado derecho.

```cpp
bool operator!=(const hash_multiset <Key, Traits, Allocator>& left, const hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto de tipo `hash_multiset`.

*Correcto*\
Objeto de tipo `hash_multiset`.

### <a name="return-value"></a>Valor devuelto

**True** si los objetos hash_multiset no son iguales; **False** si los objetos hash_multiset son iguales.

### <a name="remarks"></a>Observaciones

La comparación entre los objetos hash_multiset se basa en una comparación en pares de sus elementos. Dos objetos hash_multiset son iguales si tienen el mismo número de elementos y sus elementos respectivos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.

### <a name="example"></a>Ejemplo

```cpp
// hashset_op_ne.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1, hs2, hs3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hs1.insert ( i );
      hs2.insert ( i * i );
      hs3.insert ( i );
   }

   if ( hs1 != hs2 )
      cout << "The hash_multisets hs1 and hs2 are not equal." << endl;
   else
      cout << "The hash_multisets hs1 and hs2 are equal." << endl;

   if ( hs1 != hs3 )
      cout << "The hash_multisets hs1 and hs3 are not equal." << endl;
   else
      cout << "The hash_multisets hs1 and hs3 are equal." << endl;
}
```

```Output
The hash_multisets hs1 and hs2 are not equal.
The hash_multisets hs1 and hs3 are equal.
```

## <a name="operator-hash_multiset"></a><a name="op_eq_eq_hash_multiset"></a>operador (hash_multiset)

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_set](../standard-library/unordered-set-class.md).

Comprueba si el objeto hash_multiset del lado izquierdo del operador es igual que el objeto hash_multiset del lado derecho.

```cpp
bool operator!==(const hash_multiset <Key, Traits, Allocator>& left, const hash_multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto de tipo `hash_multiset`.

*Correcto*\
Objeto de tipo `hash_multiset`.

### <a name="return-value"></a>Valor devuelto

**True** si el objeto hash_multiset del lado izquierdo del operador es igual que el objeto hash_multiset del lado derecho del operador. En caso contrario, **False**.

### <a name="remarks"></a>Observaciones

La comparación entre los objetos hash_multiset se basa en una comparación en pares de sus elementos. Dos objetos hash_multiset son iguales si tienen el mismo número de elementos y sus elementos respectivos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.

### <a name="example"></a>Ejemplo

```cpp
// hash_multiset_op_eq.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 == s2 )
      cout << "The hash_multisets s1 and s2 are equal." << endl;
   else
      cout << "The hash_multisets s1 and s2 are not equal." << endl;

   if ( s1 == s3 )
      cout << "The hash_multisets s1 and s2 are equal." << endl;
   else
      cout << "The hash_multisets s1 and s2 are not equal." << endl;
}
```

```Output
The hash_multisets s1 and s2 are not equal.
The hash_multisets s1 and s2 are equal.
```

## <a name="see-also"></a>Consulte también

[<hash_set>](../standard-library/hash-set.md)
