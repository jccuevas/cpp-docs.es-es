---
title: Operadores de &lt;hash_map&gt;
ms.date: 11/04/2016
f1_keywords:
- hash_map/std::operator!=
- hash_map/std::operator==
ms.assetid: 24b9bb9e-e983-4060-bce5-2c7c8161ee61
ms.openlocfilehash: c4cc73feb3c8163a2be9f0122f57eaa0fb8ab3b8
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856701"
---
# <a name="lthash_mapgt-operators"></a>Operadores de &lt;hash_map&gt;

|||
|-|-|
|[operator!=](#op_neq)|[operator!= (multimap)](#op_neq_mm)|
|[operator==](#op_eq_eq)|[operator== (multimap)](#op_eq_eq_mm)|

## <a name="op_neq"></a> operator!=

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_map](unordered-map-class.md).

Comprueba si el objeto hash_map del lado izquierdo del operador no es igual que el objeto hash_map del lado derecho.

```cpp
bool operator!=(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
Objeto de tipo `hash_map`.

\ *derecha*
Objeto de tipo `hash_map`.

### <a name="return-value"></a>Valor devuelto

**True** si los objetos hash_map no son iguales; **False** si los objetos hash_map son iguales.

### <a name="remarks"></a>Observaciones

La comparación entre los objetos hash_map se basa en una comparación en pares de sus elementos. Dos objetos hash_map son iguales si tienen el mismo número de elementos y sus elementos respectivos tienen los mismos valores. Si no se cumplen estas condiciones, significa que son distintas.

Los miembros de la [< hash_map >](hash-map.md) y [< hash_set](hash-set.md) archivos de encabezado > en el [espacio de nombres stdext](stdext-namespace.md).

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

## <a name="op_eq_eq"></a>  operator==

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_map](unordered-map-class.md).

Comprueba si el objeto hash_map del lado izquierdo del operador es igual que el objeto hash_map del lado derecho.

```cpp
bool operator==(const hash_map <Key, Type, Traits, Allocator>& left, const hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
Objeto de tipo `hash_map`.

\ *derecha*
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

## <a name="op_neq_mm"></a>Operator! = (hash_multimap)

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multimap](unordered-multimap-class.md).

Comprueba si el objeto hash_multimap del lado izquierdo del operador no es igual que el objeto hash_multimap del lado derecho.

```cpp
bool operator!=(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
Objeto de tipo `hash_multimap`.

\ *derecha*
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

## <a name="op_eq_eq_mm"></a>operador = = (hash_multimap)

> [!NOTE]
> Esta API está obsoleta. La alternativa es la [clase unordered_multimap](unordered-multimap-class.md).

Comprueba si el objeto hash_multimap del lado izquierdo del operador es igual que el objeto hash_multimap del lado derecho.

```cpp
bool operator==(const hash_multimap <Key, Type, Traits, Allocator>& left, const hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
Objeto de tipo `hash_multimap`.

\ *derecha*
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
