---
title: mask_array (clase)
ms.date: 11/04/2016
f1_keywords:
- valarray/std::mask_array
helpviewer_keywords:
- mask_array class
ms.assetid: c49bed6a-3000-4f39-bff6-cb9a453acb0b
ms.openlocfilehash: 108c942bef33e44b515d46e953c9d99274e3ce8d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475830"
---
# <a name="maskarray-class"></a>mask_array (clase)

Clase de plantilla auxiliar e interna que admite objetos que son subconjuntos de valarrays principales, especificados con una expresión booleana, proporcionando operaciones entre matrices de subconjuntos.

## <a name="syntax"></a>Sintaxis

## <a name="remarks"></a>Comentarios

La clase describe un objeto que almacena una referencia a un objeto `va` de clase [valarray](../standard-library/valarray-class.md)**\<tipo >**, junto con un objeto `ba` de clase [ valarray\<bool >](../standard-library/valarray-bool-class.md), que describe la secuencia de elementos para seleccionar desde el `valarray<Type>` objeto.

Construir un `mask_array<Type>` objeto escribiendo una expresión de formato [va&#91;ba&#93;](../standard-library/valarray-class.md#op_at). Las funciones miembro de la clase mask_array se comportarán como las firmas de función correspondientes definidas para `valarray<Type>`, excepto que solo la secuencia de elementos seleccionados se ve afectada.

La secuencia consta de a lo sumo `ba.size` elementos. Un elemento *J* solo se incluye si **ba**[ *J*] es true. Por lo tanto, hay tantos elementos en la secuencia de elementos true en `ba`. Si `I` es el índice del elemento true más bajo en `ba`, a continuación, **va**[ `I`] es el elemento cero de la secuencia seleccionada.

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

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
