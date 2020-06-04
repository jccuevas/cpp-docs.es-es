---
title: indirect_array (Clase)
ms.date: 11/04/2016
f1_keywords:
- valarray/std::indirect_array
helpviewer_keywords:
- indirect_array class
ms.assetid: 10e1eaea-ba5a-405c-a25e-7bdd3eee7fc7
ms.openlocfilehash: 6be0c5153cbc94d09b414fc9e14fa498c7a4cfa7
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687922"
---
# <a name="indirect_array-class"></a>indirect_array (Clase)

Una plantilla de clase auxiliar interna que admite objetos que son subconjuntos de valarrays proporcionando operaciones entre matrices de subconjuntos definidas especificando un subconjunto de índices de una valarray primaria.

## <a name="syntax"></a>Sintaxis

## <a name="remarks"></a>Comentarios

La clase describe un objeto que almacena una referencia a un objeto `va` de la clase [valarray](../standard-library/valarray-class.md)  **\<Type >** , junto con un objeto `xa` de la clase `valarray<size_t>`, que describe la secuencia de elementos que se va a seleccionar en el objeto `valarray<Type>`.

Solo se construye un objeto `indirect_array<Type>` escribiendo una expresión con el formato `va[xa]`. Las funciones miembro de la clase indirect_array se comportarán como las signaturas de función correspondientes definidas para `valarray<Type>`, excepto en que solo la secuencia de elementos seleccionados se ve afectada.

La secuencia consta de **XA.** elementos de [tamaño](../standard-library/valarray-class.md#size) , donde el elemento `I` se convierte en el índice **XA**[`I`] dentro de `va`.

## <a name="example"></a>Ejemplo:

```cpp
// indirect_array.cpp
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

   // Select 2nd, 4th & 6th elements
   // and assign a value of 10 to them
   valarray<size_t> indx ( 3 );
   indx [0] = 2;
   indx [1] = 4;
   indx [2] = 6;
   va[indx] = 10;

   cout << "The modified operand valarray is:  ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;
}
```

### <a name="output"></a>Resultados

```cpp
The initial operand valarray is:  (0 -1 2 -1 4 -1 6 -1 8 -1).
The modified operand valarray is:  (0 -1 10 -1 10 -1 10 -1 8 -1).
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<valarray>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
