---
title: Struct logical_not | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xfunctional/std::logical_not
dev_langs:
- C++
helpviewer_keywords:
- logical_not class
- logical_not struct
ms.assetid: 892db678-31da-4540-974b-17b05efc0849
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a0d654c526e5c856431d69c045c5018d77a6fed3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="logicalnot-struct"></a>logical_not (Struct)

Objeto de función predefinido que realiza la operación NOT lógica (`operator!`) sobre su argumento.

## <a name="syntax"></a>Sintaxis

```
template <class Type = void>
struct logical_not : public unary_function<Type, bool>
{
    bool operator()(const Type& Left) const;
};

// specialized transparent functor for operator!
template <>
struct logical_not<void>
{
  template <class Type>
  auto operator()(Type&& Left) const`
     -> decltype(!std::forward<Type>(Left));
 };
```

### <a name="parameters"></a>Parámetros

`Type` Cualquier tipo que admita un `operator!` que toma un operando del tipo especificado o deducido.

`Left` El operando de la operación lógica no operación. La plantilla no especializada toma un argumento de referencia de valor L de tipo `Type`. La plantilla especializada realiza el reenvío directo de los argumentos de referencia de valor L y valor R del tipo deducido `Type`.

## <a name="return-value"></a>Valor devuelto

Resultado de `!Left`. La plantilla especializada realiza el reenvío directo del resultado, que tiene el tipo devuelto por `operator!`.

## <a name="example"></a>Ejemplo

```cpp
// functional_logical_not.cpp
// compile with: /EHsc
#include <deque>
#include <algorithm>
#include <functional>
#include <iostream>

int main( )
{
   using namespace std;
   deque<bool> d1, d2 ( 7 );
   deque<bool>::iterator iter1, iter2;

   int i;
   for ( i = 0 ; i < 7 ; i++ )
   {
      d1.push_back((bool)((i % 2) != 0));
   }

   cout << boolalpha;    // boolalpha I/O flag on

   cout << "Original deque:\n d1 = ( " ;
   for ( iter1 = d1.begin( ) ; iter1 != d1.end( ) ; iter1++ )
      cout << *iter1 << " ";
   cout << ")" << endl;

   // To flip all the truth values of the elements,
   // use the logical_not function object
   transform( d1.begin( ), d1.end( ), d2.begin( ),logical_not<bool>( ) );
   cout << "The deque with its values negated is:\n d2 = ( " ;
   for ( iter2 = d2.begin( ) ; iter2 != d2.end( ) ; iter2++ )
      cout << *iter2 << " ";
   cout << ")" << endl;
}
/* Output:
Original deque:
 d1 = ( false true false true false true false )
The deque with its values negated is:
 d2 = ( true false true false true false true )
 */
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<functional>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
