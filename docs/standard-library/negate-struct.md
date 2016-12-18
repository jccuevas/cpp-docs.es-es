---
title: "negate (Struct) | Microsoft Docs"
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
  - "negate"
  - "std.negate"
  - "std::negate"
  - "xfunctional/std::negate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "negate (struct)"
  - "negate (clase)"
ms.assetid: 8a372686-786e-4262-b37c-ca13dc11e62f
caps.latest.revision: 20
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# negate (Struct)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Objeto de función predefinido que realiza la operación de negación aritmética \(`operator-` unario\) sobre su argumento.  
  
## Sintaxis  
  
```  
template<class Type = void>  
   struct negate : public unary_function<Type, Type>   
   {  
      Type operator()(  
         const Type& Left  
      ) const;  
   };  
  
// specialized transparent functor for unary operator-  
template<>  
   struct negate<void>  
   {  
      template<class Type>  
      auto operator()(Type&& Left) const  
         -> decltype(-std::forward<Type>(Left));  
   };  
  
```  
  
#### Parámetros  
 `Type`  
 Cualquier tipo que admite un `operator-` que toma un operando del tipo especificado o deducido.  
  
 `Left`  
 Operando que se va a negar.  La plantilla especializada realiza el reenvío directo de los argumentos de referencia de valor L y valor R del tipo deducido `Type`.  
  
## Valor devuelto  
 Resultado de `-``Left.` La plantilla especializada realiza el reenvío directo del resultado, que tiene el tipo devuelto por el `operator-` unario.  
  
## Ejemplo  
  
```  
// functional_negate.cpp  
// compile with: /EHsc  
#include <vector>  
#include <functional>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
int main( )  
{  
   vector <int> v1, v2 ( 8 );  
   vector <int>::iterator Iter1, Iter2;  
  
   int i;  
   for ( i = -2 ; i <= 5 ; i++ )  
   {  
      v1.push_back( 5 * i );  
   }  
  
   cout << "The vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // Finding the element-wise negatives of the vector v1  
   transform ( v1.begin( ),  v1.end( ), v2.begin( ), negate<int>( ) );  
  
   cout << "The negated elements of the vector = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")" << endl;  
}  
```  
  
  **The vector v1 \= \( \-10 \-5 0 5 10 15 20 25 \)**  
**The negated elements of the vector \= \( 10 5 0 \-5 \-10 \-15 \-20 \-25 \)**   
## Requisitos  
 **Encabezado:** \<functional\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)