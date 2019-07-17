---
title: greater (struct)
ms.date: 11/04/2016
f1_keywords:
- functional/std::greater
helpviewer_keywords:
- greater struct
- greater function
ms.assetid: ebc348e1-edcd-466b-b21a-db95bd8f9079
ms.openlocfilehash: aca47223810bdae31e7711492d107fbfa2814391
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243728"
---
# <a name="greater-struct"></a>greater (struct)

Predicado binario que realiza la operación mayor que (`operator>`) sobre sus argumentos.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Type = void>
struct greater : public binary_function <Type, Type, bool>
{
    bool operator()(
    const Type& Left,
    const Type& Right) const;

};

// specialized transparent functor for operator>
template <>
struct greater<void>
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const
    ->  decltype(std::forward<T>(Left)> std::forward<U>(Right));
};
```

### <a name="parameters"></a>Parámetros

*Tipo*, *T*, *U*\
Cualquier tipo que admite un `operator>` que toma operandos de los tipos especificados o deducidos.

*Izquierda*\
Operando izquierdo de la operación mayor que. La plantilla no especializada toma un argumento de referencia de valor l de tipo *tipo*. La plantilla especializada realiza el reenvío de valor l directo y los argumentos de referencia de valor r del tipo deducen *T*.

*Correcto*\
Operando derecho de la operación mayor que. La plantilla no especializada toma un argumento de referencia de valor l de tipo *tipo*. La plantilla especializada realiza el reenvío de valor l directo y los argumentos de referencia de valor r del tipo deducen *U*.

## <a name="return-value"></a>Valor devuelto

Resultado de `Left > Right`. La plantilla especializada realiza el reenvío directo del resultado, que tiene el tipo devuelto por `operator>`.

## <a name="remarks"></a>Comentarios

El predicado binario `greater` < `Type`> proporciona una ordenación débil estricta de un conjunto de valores de elemento de tipo *tipo* en clases de equivalencia, si y solo si este tipo satisface el estándar de matemático requisitos para lo que se ordenan. Las especializaciones para cualquier tipo de puntero producen una ordenación total de los elementos, en la que todos los elementos de valores distintos están ordenados unos con respecto a otros.

## <a name="example"></a>Ejemplo

```cpp
// functional_greater.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <cstdlib>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter1;

   int i;
   for ( i = 0 ; i < 8 ; i++ )
   {
      v1.push_back( rand( ) );
   }

   cout << "Original vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in ascending order,
   // use default binary predicate less<int>( )
   sort( v1.begin( ), v1.end( ) );
   cout << "Sorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   // To sort in descending order,
   // specify binary predicate greater<int>( )
   sort( v1.begin( ), v1.end( ), greater<int>( ) );
   cout << "Resorted vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;
}
```

```Output
Original vector v1 = (41 18467 6334 26500 19169 15724 11478 29358)
Sorted vector v1 = (41 6334 11478 15724 18467 19169 26500 29358)
Resorted vector v1 = (29358 26500 19169 18467 15724 11478 6334 41)
```
