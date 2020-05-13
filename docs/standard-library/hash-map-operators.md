---
title: Operadores de &lt;hash_map&gt;
ms.date: 11/04/2016
f1_keywords:
- hash_map/std::operator!=
- hash_map/std::operator==
ms.assetid: 24b9bb9e-e983-4060-bce5-2c7c8161ee61
ms.openlocfilehash: ed143349f3afc7a27ad565c1cc929c6ecb5f6ad8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375448"
---
# <a name="lthash_mapgt-operators"></a>Operadores de &lt;hash_map&gt;

|||
|-|-|
|[¡Operador!](#op_neq)|[operador! (multimapa)](#op_neq_mm)|
|[operadora](#op_eq_eq)|[operador (multimapa)](#op_eq_eq_mm)|

## <a name="operator"></a><a name="op_neq"></a>¡Operador!

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_map](unordered-map-class.md).

Comprueba si el objeto hash_map del lado izquierdo del operador no es igual que el objeto hash_map del lado derecho.

```cpp
bool operator!=(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto de tipo `hash_map`.

*Correcto*\
Objeto de tipo `hash_map`.

### <a name="return-value"></a>Valor devuelto

**True** si los objetos hash_map no son iguales; **False** si los objetos hash_map son iguales.

### <a name="remarks"></a>Observaciones

La comparación entre los objetos hash_map se basa en una comparación en pares de sus elementos. Dos objetos hash_map son iguales si tienen el mismo número de elementos y sus elementos respectivos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.

Los miembros de la [>de hash_map de<](hash-map.md) y<hash_set archivos de encabezado de [>](hash-set.md) en el espacio de [nombres stdext](stdext-namespace.md).

### <a name="example"></a>Ejemplo

```cpp
// hash_map_op_ne.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1, hm2, hm3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hm1.insert ( Int_Pair ( i, i ) );
      hm2.insert ( Int_Pair ( i, i * i ) );
      hm3.insert ( Int_Pair ( i, i ) );
   }

   if ( hm1 != hm2 )
      cout << "The hash_maps hm1 and hm2 are not equal." << endl;
   else
      cout << "The hash_maps hm1 and hm2 are equal." << endl;

   if ( hm1 != hm3 )
      cout << "The hash_maps hm1 and hm3 are not equal." << endl;
   else
      cout << "The hash_maps hm1 and hm3 are equal." << endl;
}
```

```Output
The hash_maps hm1 and hm2 are not equal.
The hash_maps hm1 and hm3 are equal.
```

## <a name="operator"></a><a name="op_eq_eq"></a>operadora

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_map](unordered-map-class.md).

Comprueba si el objeto hash_map del lado izquierdo del operador es igual que el objeto hash_map del lado derecho.

```cpp
bool operator==(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto de tipo `hash_map`.

*Correcto*\
Objeto de tipo `hash_map`.

### <a name="return-value"></a>Valor devuelto

**True** si el objeto hash_map del lado izquierdo del operador es igual que el objeto hash_map del lado derecho del operador. En caso contrario, **False**.

### <a name="remarks"></a>Observaciones

La comparación entre los objetos hash_map se basa en una comparación en pares de sus elementos. Dos objetos hash_map son iguales si tienen el mismo número de elementos y sus elementos respectivos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.

### <a name="example"></a>Ejemplo

```cpp
// hash_map_op_eq.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1, hm2, hm3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hm1.insert ( Int_Pair ( i, i ) );
      hm2.insert ( Int_Pair ( i, i * i ) );
      hm3.insert ( Int_Pair ( i, i ) );
   }

   if ( hm1 == hm2 )
      cout << "The hash_maps hm1 and hm2 are equal." << endl;
   else
      cout << "The hash_maps hm1 and hm2 are not equal." << endl;

   if ( hm1 == hm3 )
      cout << "The hash_maps hm1 and hm3 are equal." << endl;
   else
      cout << "The hash_maps hm1 and hm3 are not equal." << endl;
}
```

```Output
The hash_maps hm1 and hm2 are not equal.
The hash_maps hm1 and hm3 are equal.
```

## <a name="operator-hash_multimap"></a><a name="op_neq_mm"></a>operador! (hash_multimap)

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](unordered-multimap-class.md).

Comprueba si el objeto hash_multimap del lado izquierdo del operador no es igual que el objeto hash_multimap del lado derecho.

```cpp
bool operator!=(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto de tipo `hash_multimap`.

*Correcto*\
Objeto de tipo `hash_multimap`.

### <a name="return-value"></a>Valor devuelto

**True** si los objetos hash_multimap no son iguales; **False** si los objetos hash_multimap son iguales.

### <a name="remarks"></a>Observaciones

La comparación entre los objetos hash_multimap se basa en una comparación en pares de sus elementos. Dos objetos hash_multimap son iguales si tienen el mismo número de elementos y sus elementos respectivos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.

### <a name="example"></a>Ejemplo

```cpp
// hash_multimap_op_ne.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1, hm2, hm3;
   int i;
   typedef pair <int, int> Int_Pair;

   for ( i = 0 ; i < 3 ; i++ )
   {
      hm1.insert ( Int_Pair ( i, i ) );
      hm2.insert ( Int_Pair ( i, i * i ) );
      hm3.insert ( Int_Pair ( i, i ) );
   }

   if ( hm1 != hm2 )
      cout << "The hash_multimaps hm1 and hm2 are not equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm2 are equal." << endl;

   if ( hm1 != hm3 )
      cout << "The hash_multimaps hm1 and hm3 are not equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm3 are equal." << endl;
}
```

```Output
The hash_multimaps hm1 and hm2 are not equal.
The hash_multimaps hm1 and hm3 are equal.
```

## <a name="operator--hash_multimap"></a><a name="op_eq_eq_mm"></a>operador (hash_multimap)

> [!NOTE]
> Esta API está obsoleta. La alternativa es [unordered_multimap Class](unordered-multimap-class.md).

Comprueba si el objeto hash_multimap del lado izquierdo del operador es igual que el objeto hash_multimap del lado derecho.

```cpp
bool operator==(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto de tipo `hash_multimap`.

*Correcto*\
Objeto de tipo `hash_multimap`.

### <a name="return-value"></a>Valor devuelto

**True** si el objeto hash_multimap del lado izquierdo del operador es igual que el objeto hash_multimap del lado derecho del operador. En caso contrario, **False**.

### <a name="remarks"></a>Observaciones

La comparación entre los objetos hash_multimap se basa en una comparación en pares de sus elementos. Dos objetos hash_multimap son iguales si tienen el mismo número de elementos y sus elementos respectivos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.

### <a name="example"></a>Ejemplo

```cpp
// hash_multimap_op_eq.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap<int, int> hm1, hm2, hm3;
   int i;
   typedef pair<int, int> Int_Pair;

   for (i = 0; i < 3; i++)
   {
      hm1.insert(Int_Pair(i, i));
      hm2.insert(Int_Pair(i, i*i));
      hm3.insert(Int_Pair(i, i));
   }

   if ( hm1 == hm2 )
      cout << "The hash_multimaps hm1 and hm2 are equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm2 are not equal." << endl;

   if ( hm1 == hm3 )
      cout << "The hash_multimaps hm1 and hm3 are equal." << endl;
   else
      cout << "The hash_multimaps hm1 and hm3 are not equal." << endl;
}
```

```Output
The hash_multimaps hm1 and hm2 are not equal.
The hash_multimaps hm1 and hm3 are equal.
```

## <a name="see-also"></a>Consulte también

[<hash_map>](hash-map.md)
