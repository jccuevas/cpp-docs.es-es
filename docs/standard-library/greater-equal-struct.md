---
title: greater_equal (Struct) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- greater_equal
- xfunctional/std::greater_equal
dev_langs:
- C++
helpviewer_keywords:
- greater_equal struct
- greater_equal function
ms.assetid: a8ba911b-7af8-4653-b972-d8618f4df7d5
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 2d05749ba2837a3879c91886b9266de47dd2ece6
ms.openlocfilehash: 56fd730319f7523915fcdbb71d9cd97c98fda5b0
ms.lasthandoff: 02/24/2017

---
# <a name="greaterequal-struct"></a>greater_equal (Struct)
Predicado binario que realiza la operación mayor o igual que (`operator>=`) sobre sus argumentos.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class Type = void>
struct greater_equal : public binary_function <Type, Type, bool>  
{
    bool operator()(const Type& Left, const Type& Right) const;
};

// specialized transparent functor for operator>=
template <>
struct greater_equal<void>  
{
  template <class T, class U>
  auto operator()(T&& Left, U&& Right) const`
    -> decltype(std::forward<T>(Left)>= std::forward<U>(Right));
 };
```  
  
#### <a name="parameters"></a>Parámetros  
 `Type`, `T`, `U`  
 Cualquier tipo que admite un `operator>=` que toma operandos de los tipos especificados o deducidos.  
  
 `Left`  
 Operando izquierdo de la operación mayor o igual que. La plantilla no especializada toma un argumento de referencia de valor L de tipo `Type`. La plantilla especializada realiza el reenvío directo de los argumentos de referencia de valor L y valor R del tipo deducido `T`.  
  
 `Right`  
 Operando derecho de la operación mayor o igual que. La plantilla no especializada toma un argumento de referencia de valor L de tipo `Type`. La plantilla especializada realiza el reenvío directo de los argumentos de referencia de valor L y valor R del tipo deducido `U`.  
  
## <a name="return-value"></a>Valor devuelto  
 Resultado de `Left``>=``Right`. La plantilla especializada realiza el reenvío directo del resultado, que tiene el tipo devuelto por `operator>=`.  
  
## <a name="remarks"></a>Comentarios  
 El predicado binario `greater_equal`< `Type`> proporciona una ordenación débil estricta de un conjunto de valores de elementos de tipo `Type` en clases de equivalencia, si y solo si este tipo satisface los requisitos matemáticos estándar para que se pueda ordenar de esa forma. Las especializaciones para cualquier tipo de puntero producen una ordenación total de los elementos, en la que todos los elementos de valores distintos están ordenados unos con respecto a otros.  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
// functional_greater_equal.cpp  
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
   v1.push_back( 6262 );  
   v1.push_back( 6262 );  
   for ( i = 0 ; i < 5 ; i++ )  
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
   // specify binary predicate greater_equal<int>( )  
   sort( v1.begin( ), v1.end( ), greater_equal<int>( ) );  
   cout << "Resorted vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
}  
```  
  
## <a name="output"></a>Salida  
  
```
Original vector v1 = (6262 6262 41 18467 6334 26500 19169)
Sorted vector v1 = (41 6262 6262 6334 18467 19169 26500)
Resorted vector v1 = (26500 19169 18467 6334 6262 6262 41)
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<functional>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)




