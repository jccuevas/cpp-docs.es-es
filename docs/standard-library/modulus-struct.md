---
title: modulus (Struct) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xfunctional/std::modulus
dev_langs:
- C++
helpviewer_keywords:
- modulus class
- modulus struct
ms.assetid: 86d342f7-b7b1-46a4-b0bb-6b7ae827369b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8b277a31eafafa4ae33066653b7a080bb3474408
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "44104126"
---
# <a name="modulus-struct"></a>modulus (struct)

Objeto de función predefinido que realiza la operación de división del módulo (`operator%`) sobre sus argumentos.

## <a name="syntax"></a>Sintaxis

```
template <class Type = void>
struct modulus : public binary_function <Type, Type, Type>
{
    Type operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator%
template <>
struct modulus<void>
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const`
    -> decltype(std::forward<T>(Left) % std::forward<U>(Right));
};
```

### <a name="parameters"></a>Parámetros

*Tipo*, *T*, *U* cualquier tipo que admita un `operator%` que toma operandos de los tipos especificados o deducidos.

*Izquierda*<br/>
Operando izquierdo de la operación de módulo. La plantilla no especializada toma un argumento de referencia de valor l de tipo *tipo*. La plantilla especializada realiza el reenvío de valor l directo y los argumentos de referencia de valor r del tipo deducen *T*.

*Derecha*<br/>
Operando derecho de la operación de módulo. La plantilla no especializada toma un argumento de referencia de valor l de tipo *tipo*. La plantilla especializada realiza el reenvío de valor l directo y los argumentos de referencia de valor r del tipo deducen *U*.

## <a name="return-value"></a>Valor devuelto

Resultado de `Left % Right`. La plantilla especializada realiza el reenvío directo del resultado, que tiene el tipo devuelto por `operator%`.

## <a name="remarks"></a>Comentarios

El functor de `modulus` está limitado a tipos enteros para los tipos de datos básicos, o a tipos definidos por el usuario que implementan el `operator%`.

## <a name="example"></a>Ejemplo

```cpp
// functional_modulus.cpp
// compile with: /EHsc
#include <vector>
#include <functional>
#include <algorithm>
#include <iostream>

using namespace std;

int main( )
{
   vector <int> v1, v2, v3 ( 6 );
   vector <int>::iterator Iter1, Iter2, Iter3;

   int i;
   for ( i = 1 ; i <= 6 ; i++ )
   {
      v1.push_back( 5 * i );
   }

   int j;
   for ( j = 1 ; j <= 6 ; j++ )
   {
      v2.push_back( 3 * j );
   }

   cout << "The vector v1 = ( " ;
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
      cout << *Iter1 << " ";
   cout << ")" << endl;

   cout << "The vector v2 = ( " ;
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
      cout << *Iter2 << " ";
   cout << ")" << endl;

   // Finding the element-wise remainders of the elements of v1 & v2
   transform (v1.begin( ),  v1.end( ), v2.begin( ), v3.begin ( ),
      modulus<int>() );

   cout << "The element-wise remainders of the modular division\n are: ( " ;
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
      cout << *Iter3 << " ";
   cout << ")" << endl;
}
/* Output:
The vector v1 = ( 5 10 15 20 25 30 )
The vector v2 = ( 3 6 9 12 15 18 )
The element-wise remainders of the modular division
are: ( 2 4 6 8 10 12 )
*/
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<functional>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
