---
title: minus (Struct) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xfunctional/std::minus
dev_langs: C++
helpviewer_keywords:
- minus struct
- minus class
ms.assetid: 7bce784e-2be6-413a-b516-004e9ecb2a39
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 339577e11ac377bf8062860e2ebe307c798f9b49
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="minus-struct"></a>minus (Struct)
Objeto de función predefinido que realiza la operación de resta (`operator-` binario) sobre sus argumentos.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class Type = void>
struct minus : public binary_function <Type, Type, Type>  
{
    Type operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator-
template <>
struct minus<void>  
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const`
    -> decltype(std::forward<T>(Left) - std::forward<U>(Right));
 };
```  
  
#### <a name="parameters"></a>Parámetros  
 `Type`, `T`, `U`  
 Tipo que admite un `operator-` binario que toma operandos de los tipos especificados o deducidos.  
  
 `Left`  
 Operando izquierdo de la operación. La plantilla no especializada toma un argumento de referencia de valor L de tipo `Type`. La plantilla especializada realiza el reenvío directo de los argumentos de referencia de valor L y valor R del tipo deducido `T`.  
  
 `Right`  
 Operando derecho de la operación. La plantilla no especializada toma un argumento de referencia de valor L de tipo `Type`. La plantilla especializada realiza el reenvío directo de los argumentos de referencia de valor L y valor R del tipo deducido `U`.  
  
## <a name="return-value"></a>Valor devuelto  
 Resultado de `Left - Right`. La plantilla especializada realiza el reenvío directo del resultado, que tiene el tipo devuelto por `operator-`.  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
// functional_minus.cpp  
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
   for ( i = 0 ; i <= 5 ; i++ )  
   {  
      v1.push_back( 4 * i + 1);  
   }  
  
   int j;  
   for ( j = 0 ; j <= 5 ; j++ )  
   {  
      v2.push_back( 3 * j - 1);  
   }  
  
   cout << "The vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   cout << "The vector v2 = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")" << endl;  
  
   // Finding the element-wise diference of the elements of v1 & v2  
   transform ( v1.begin( ),  v1.end( ), v2.begin( ), v3.begin ( ),   
      minus<int>( ) );  
  
   cout << "The element-wise differences between v1 and v2 are: ( " ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )  
      cout << *Iter3 << " ";  
   cout << ")" << endl;  
}  
\* Output:   
The vector v1 = ( 1 5 9 13 17 21 )  
The vector v2 = ( -1 2 5 8 11 14 )  
The element-wise differences between v1 and v2 are: ( 2 3 4 5 6 7 )  
*\  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<functional>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)



