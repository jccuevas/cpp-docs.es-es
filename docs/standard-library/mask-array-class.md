---
title: mask_array (clase)
ms.date: 11/04/2016
f1_keywords:
- valarray/std::mask_array
helpviewer_keywords:
- mask_array class
ms.assetid: c49bed6a-3000-4f39-bff6-cb9a453acb0b
ms.openlocfilehash: 9da5e3593288be02819330e11b60e306784054dc
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460139"
---
# <a name="maskarray-class"></a>mask_array (clase)

Clase de plantilla auxiliar e interna que admite objetos que son subconjuntos de valarrays principales, especificados con una expresión booleana, proporcionando operaciones entre matrices de subconjuntos.

## <a name="syntax"></a>Sintaxis

## <a name="remarks"></a>Comentarios

La clase describe un objeto que almacena una referencia a un objeto `va` de la clase [valarray](../standard-library/valarray-class.md) **\<Type >** , junto con un `ba` objeto de la clase [valarray\<bool >](../standard-library/valarray-bool-class.md), que describe el secuencia de elementos que se van a `valarray<Type>` seleccionar en el objeto.

Solo se construye `mask_array<Type>` un objeto escribiendo una expresión con el formato [va&#91;BA&#93;](../standard-library/valarray-class.md#op_at). Las funciones miembro de la clase mask_array se comportarán como las signaturas de `valarray<Type>`función correspondientes definidas para, excepto en que solo la secuencia de elementos seleccionados se ve afectada.

La secuencia consta de como máximo `ba.size` elementos. Un elemento *J* solo se incluye si **ba**[ *J*] es true. Por lo tanto, hay tantos elementos en la secuencia, ya que hay elementos `ba`verdaderos en. Si `I` es el índice del elemento true más bajo de `ba`, **va**[ `I`] es el elemento cero de la secuencia seleccionada.

## <a name="example"></a>Ejemplo

```cpp
// mask_array.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      va [ i ] =  i;
   for ( i = 1 ; i < 10 ; i += 2 )
      va [ i ] =  -1;

   cout << "The initial operand valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   // Use masked subsets to assign a value of 10
   // to all elements grrater than 3 in value
   va [va > 3 ] = 10;
   cout << "The modified operand valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;
}
```

### <a name="output"></a>Salida

```Output
The initial operand valarray is:  (0 -1 2 -1 4 -1 6 -1 8 -1).
The modified operand valarray is:  (0 -1 2 -1 10 -1 10 -1 10 -1).
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<valarray>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
