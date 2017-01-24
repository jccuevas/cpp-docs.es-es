---
title: "minus (Struct) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "minus"
  - "std.minus"
  - "std::minus"
  - "xfunctional/std::minus"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "minus (struct)"
  - "minus (clase)"
ms.assetid: 7bce784e-2be6-413a-b516-004e9ecb2a39
caps.latest.revision: 20
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# minus (Struct)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Objeto de función predefinido que realiza la operación de resta \(`operator-` binario\) sobre sus argumentos.  
  
## Sintaxis  
  
```  
template<class Type = void>  
   struct minus : public binary_function <Type, Type, Type>   
   {  
      Type operator()(  
         const Type& Left,   
         const Type& Right  
      ) const;  
   };  
  
// specialized transparent functor for operator-  
template<>  
   struct minus<void>  
   {  
      template<class Type1, class Type2>  
      auto operator()(Type1&& Left, Type2&& Right) const  
         -> decltype(std::forward<Type1>(Left)  
            - std::forward<Type2>(Right));  
   };  
  
```  
  
#### Parámetros  
 `Type`, `Type1`, `Type2`  
 Tipo que admite un `operator-` binario que toma operandos de los tipos especificados o deducidos.  
  
 `Left`  
 Operando izquierdo de la operación.  La plantilla no especializada toma un argumento de referencia de valor L de tipo `Type`.  La plantilla especializada realiza el reenvío directo de los argumentos de referencia de valor L y valor R del tipo deducido `Type1`.  
  
 `Right`  
 Operando derecho de la operación.  La plantilla no especializada toma un argumento de referencia de valor L de tipo `Type`.  La plantilla especializada realiza el reenvío directo de los argumentos de referencia de valor L y valor R del tipo deducido `Type2`.  
  
## Valor devuelto  
 Resultado de `Left` `-` `Right`.  La plantilla especializada realiza el reenvío directo del resultado, que tiene el tipo devuelto por `operator-`.  
  
## Ejemplo  
  
```  
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
```  
  
  **The vector v1 \= \( 1 5 9 13 17 21 \)**  
**The vector v2 \= \( \-1 2 5 8 11 14 \)**  
**The element\-wise differences between v1 and v2 are: \( 2 3 4 5 6 7 \)**   
## Requisitos  
 **Encabezado:** \<functional\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)