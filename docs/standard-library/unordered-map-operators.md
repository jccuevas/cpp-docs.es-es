---
title: Operadores de &lt;unordered_map&gt;
ms.date: 11/04/2016
f1_keywords:
- unordered_map/std::operator!=
- unordered_map/std::operator==
ms.assetid: 9d5add0b-84bd-4a79-bd82-3f58b55145ed
ms.openlocfilehash: f062c4fd0332525a8b8940d2d93df41df56d2baa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373124"
---
# <a name="ltunordered_mapgt-operators"></a>Operadores de &lt;unordered_map&gt;

|||||
|-|-|-|-|
|[¡Operador!](#op_neq)|[operadora](#op_eq_eq)|[¡Operador!](#op_neq_multimap)|[operadora](#op_eq_eq_multimap)|

## <a name="operator"></a><a name="op_neq"></a>¡Operador!

Comprueba si el objeto [unordered_map](../standard-library/unordered-map-class.md) del lado izquierdo del operador no es igual que el objeto unordered_map del lado derecho.

```cpp
bool operator!=(const unordered_map <Key, Type, Hash, Pred, Allocator>& left, const unordered_map <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto de tipo `unordered_map`.

*Correcto*\
Objeto de tipo `unordered_map`.

### <a name="return-value"></a>Valor devuelto

**true** si los unordered_maps no son iguales; **falso** si son iguales.

### <a name="remarks"></a>Observaciones

La comparación entre los objetos unordered_map no se ve afectada por el orden arbitrario en el que almacenan sus elementos. Dos unordered_map son iguales si tienen el mismo número de elementos y los elementos de un contenedor son una permutación de los elementos del otro contenedor. Si no se cumplen estas condiciones, significa que son distintas.

### <a name="example"></a>Ejemplo

```cpp
// unordered_map_op_ne.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_map>
#include <iostream>
#include <ios>

int main( )
{
   using namespace std;
   unordered_map<int, int> um1, um2, um3;

   for ( int i = 0 ; i < 3 ; ++i ) {
      um1.insert( make_pair( i+1, i ) );
      um1.insert( make_pair( i, i ) );

      um2.insert( make_pair( i, i+1 ) );
      um2.insert( make_pair( i, i ) );

      um3.insert( make_pair( i, i ) );
      um3.insert( make_pair( i+1, i ) );
   }

   cout << boolalpha;
   cout << "um1 != um2: " << (um1 != um2) << endl;
   cout << "um1 != um3: " << (um1 != um3) << endl;
   cout << "um2 != um3: " << (um2 != um3) << endl;
}
```

**Salida:**

`um1 != um2: true`

`um1 != um3: false`

`um2 != um3: true`

## <a name="operator"></a><a name="op_eq_eq"></a>operadora

Comprueba si el objeto [unordered_map](../standard-library/unordered-map-class.md) del lado izquierdo del operador es igual que el objeto unordered_map del lado derecho.

```cpp
bool operator==(const unordered_map <Key, Type, Hash, Pred, Allocator>& left, const unordered_map <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto de tipo `unordered_map`.

*Correcto*\
Objeto de tipo `unordered_map`.

### <a name="return-value"></a>Valor devuelto

**true** si los unordered_maps son iguales; **falso** si no son iguales.

### <a name="remarks"></a>Observaciones

La comparación entre los objetos unordered_map no se ve afectada por el orden arbitrario en el que almacenan sus elementos. Dos unordered_map son iguales si tienen el mismo número de elementos y los elementos de un contenedor son una permutación de los elementos del otro contenedor. Si no se cumplen estas condiciones, significa que son distintas.

### <a name="example"></a>Ejemplo

```cpp
// unordered_map_op_eq.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_map>
#include <iostream>
#include <ios>

int main( )
{
   using namespace std;
   unordered_map<int, int> um1, um2, um3;

   for ( int i = 0 ; i < 3 ; ++i ) {
      um1.insert( make_pair( i+1, i ) );
      um1.insert( make_pair( i, i ) );

      um2.insert( make_pair( i, i+1 ) );
      um2.insert( make_pair( i, i ) );

      um3.insert( make_pair( i, i ) );
      um3.insert( make_pair( i+1, i ) );
   }

   cout << boolalpha;
   cout << "um1 == um2: " << (um1 == um2) << endl;
   cout << "um1 == um3: " << (um1 == um3) << endl;
   cout << "um2 == um3: " << (um2 == um3) << endl;
}
```

**Salida:**

`um1 == um2: false`

`um1 == um3: true`

`um2 == um3: false`

## <a name="operator"></a><a name="op_neq_multimap"></a>¡Operador!

Comprueba si el objeto [unordered_multimap](../standard-library/unordered-multimap-class.md) del lado izquierdo del operador no es igual que el objeto unordered_multimap del lado derecho.

```cpp
bool operator!=(const unordered_multimap <Key, Type, Hash, Pred, Allocator>& left, const unordered_multimap <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto de tipo `unordered_multimap`.

*Correcto*\
Objeto de tipo `unordered_multimap`.

### <a name="return-value"></a>Valor devuelto

**true** si los unordered_multimaps no son iguales; **falso** si son iguales.

### <a name="remarks"></a>Observaciones

La comparación entre los objetos unordered_multimap no se ve afectada por el orden arbitrario en el que almacenan sus elementos. Dos unordered_multimap son iguales si tienen el mismo número de elementos y los elementos de un contenedor son una permutación de los elementos del otro contenedor. De lo contrario, no son iguales.

### <a name="example"></a>Ejemplo

```cpp
// unordered_multimap_op_ne.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_map>
#include <iostream>
#include <ios>

int main( )
{
   using namespace std;
   unordered_multimap<int, int> um1, um2, um3;

   for ( int i = 0 ; i < 3 ; ++i ) {
      um1.insert( make_pair( i, i ) );
      um1.insert( make_pair( i, i ) );

      um2.insert( make_pair( i, i ) );
      um2.insert( make_pair( i, i ) );
      um2.insert( make_pair( i, i ) );

      um3.insert( make_pair( i, i ) );
      um3.insert( make_pair( i, i ) );
   }

   cout << boolalpha;
   cout << "um1 != um2: " << (um1 != um2) << endl;
   cout << "um1 != um3: " << (um1 != um3) << endl;
   cout << "um2 != um3: " << (um2 != um3) << endl;
}
```

**Salida:**

`um1 != um2: true`

`um1 != um3: false`

`um2 != um3: true`

## <a name="operator"></a><a name="op_eq_eq_multimap"></a>operadora

Comprueba si el objeto [unordered_multimap](../standard-library/unordered-multimap-class.md) del lado izquierdo del operador es igual que el objeto unordered_multimap del lado derecho.

```cpp
bool operator==(const unordered_multimap <Key, Type, Hash, Pred, Allocator>& left, const unordered_multimap <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto de tipo `unordered_multimap`.

*Correcto*\
Objeto de tipo `unordered_multimap`.

### <a name="return-value"></a>Valor devuelto

**true** si los unordered_multimaps son iguales; **falso** si no son iguales.

### <a name="remarks"></a>Observaciones

La comparación entre los objetos unordered_multimap no se ve afectada por el orden arbitrario en el que almacenan sus elementos. Dos unordered_multimap son iguales si tienen el mismo número de elementos y los elementos de un contenedor son una permutación de los elementos del otro contenedor. Si no se cumplen estas condiciones, significa que son distintas.

### <a name="example"></a>Ejemplo

```cpp
// unordered_multimap_op_eq.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_map>
#include <iostream>
#include <ios>

int main( )
{
   using namespace std;
   unordered_multimap<int, int> um1, um2, um3;

   for ( int i = 0 ; i < 3 ; ++i ) {
      um1.insert( make_pair( i, i ) );
      um1.insert( make_pair( i, i ) );

      um2.insert( make_pair( i, i ) );
      um2.insert( make_pair( i, i ) );
      um2.insert( make_pair( i, i ) );

      um3.insert( make_pair( i, i ) );
      um3.insert( make_pair( i, i ) );
   }

   cout << boolalpha;
   cout << "um1 == um2: " << (um1 == um2) << endl;
   cout << "um1 == um3: " << (um1 == um3) << endl;
   cout << "um2 == um3: " << (um2 == um3) << endl;
}
```

**Salida:**

`um1 == um2: false`

`um1 == um3: true`

`um2 == um3: false`

## <a name="see-also"></a>Consulte también

[<unordered_map>](../standard-library/unordered-map.md)
