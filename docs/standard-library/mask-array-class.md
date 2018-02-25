---
title: Clase mask_array | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- valarray/std::mask_array
dev_langs:
- C++
helpviewer_keywords:
- mask_array class
ms.assetid: c49bed6a-3000-4f39-bff6-cb9a453acb0b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 768ad87caf6fb3d5b8ed5574bd5f110282d795f5
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="maskarray-class"></a>mask_array (Clase)
Clase de plantilla auxiliar e interna que admite objetos que son subconjuntos de valarrays principales, especificados con una expresión booleana, proporcionando operaciones entre matrices de subconjuntos.  
  
## <a name="syntax"></a>Sintaxis  
  
  
  
## <a name="remarks"></a>Comentarios  
 La clase describe un objeto que almacena una referencia a un objeto **va** de la clase [valarray](../standard-library/valarray-class.md)**\<Type>**, junto con un objeto **ba** de la clase [valarray\<bool>](../standard-library/valarray-bool-class.md), que describe la secuencia de los elementos que se pueden seleccionar desde el objeto **valarray\<Type>**.  
  
 La única manera de construir un objeto **mask_array\<Type>** consiste en escribir una expresión de formato [va&#91;ba&#93;](../standard-library/valarray-class.md#op_at). Las funciones miembro de la clase mask_array se comportarán como las firmas de función correspondientes definidas para **valarray\<Type>**, excepto en que solo la secuencia de elementos seleccionados se ve afectada.  
  
 La secuencia consta como máximo de elementos **ba.size** . Un elemento *J* solo se incluye si **ba**[ *J*] es true. Por lo tanto, hay tantos elementos en la secuencia de elementos true en **ba**. Si `I` es el índice del elemento true más bajo en **ba**, **va**[ `I`] es el elemento cero de la secuencia seleccionada.  
  
## <a name="example"></a>Ejemplo:  
  
```  
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
  
```  
The initial operand valarray is:  (0 -1 2 -1 4 -1 6 -1 8 -1).  
The modified operand valarray is:  (0 -1 2 -1 10 -1 10 -1 10 -1).  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<valarray>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

