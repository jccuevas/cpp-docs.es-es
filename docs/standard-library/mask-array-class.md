---
title: mask_array (clase)
ms.date: 11/04/2016
f1_keywords:
- valarray/std::mask_array
helpviewer_keywords:
- mask_array class
ms.assetid: c49bed6a-3000-4f39-bff6-cb9a453acb0b
ms.openlocfilehash: 12398203d61f2c3ea155b5f6e6e7b118d4a13c75
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689401"
---
# <a name="mask_array-class"></a>mask_array (clase)

Una plantilla de clase auxiliar interna que admite objetos que son subconjuntos de valarrays principales, especificados con una expresión booleana, proporcionando operaciones entre las matrices de subconjuntos.

## <a name="syntax"></a>Sintaxis

## <a name="remarks"></a>Comentarios

La clase describe un objeto que almacena una referencia a un objeto `va` de la clase [valarray](../standard-library/valarray-class.md)  **\<Type >** , junto con un objeto `ba` de la clase [valarray \<bool](../standard-library/valarray-bool-class.md)>, que describe la secuencia de elementos que se van a seleccionar. del objeto `valarray<Type>`.

Solo se crea un objeto `mask_array<Type>` escribiendo una expresión con el formato [va&#91;BA&#93;](../standard-library/valarray-class.md#op_at). Las funciones miembro de la clase mask_array se comportarán como las signaturas de función correspondientes definidas para `valarray<Type>`, excepto en que solo la secuencia de elementos seleccionados se ve afectada.

La secuencia consta de a lo sumo `ba.size` elementos. Un elemento *J* solo se incluye si **ba**[ *J*] es true. Por lo tanto, hay tantos elementos en la secuencia, ya que hay elementos verdaderos en `ba`. Si `I` es el índice del elemento true más bajo de `ba`, **va**[`I`] es el elemento cero de la secuencia seleccionada.

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

### <a name="output"></a>Resultados

```Output
The initial operand valarray is:  (0 -1 2 -1 4 -1 6 -1 8 -1).
The modified operand valarray is:  (0 -1 2 -1 10 -1 10 -1 10 -1).
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<valarray>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
