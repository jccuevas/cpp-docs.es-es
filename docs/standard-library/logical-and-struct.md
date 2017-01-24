---
title: "logical_and (Struct) | Microsoft Docs"
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
  - "std::logical_and"
  - "xfunctional/std::logical_and"
  - "std.logical_and"
  - "logical_and"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "logical_and (clase)"
  - "logical_and (struct)"
ms.assetid: 1a375cc2-0592-4d57-a553-78009c7ad610
caps.latest.revision: 22
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# logical_and (Struct)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Objeto de función predefinido que realiza la operación de conjunción lógica \(`operator&&`\) sobre sus argumentos.  
  
## Sintaxis  
  
```  
template<class Type = void>  
   struct logical_and : public binary_function<Type, Type, bool>   
   {  
      bool operator()(  
         const Type& Left,   
         const Type& Right  
      ) const;  
   };  
  
// specialized transparent functor for operator&&  
template<>  
   struct logical_and<void>  
   {  
      template<class Type1, class Type2>  
      auto operator()(Type1&& Left, Type2&& Right) const  
         -> decltype(std::forward<Type1>(Left)  
            && std::forward<Type2>(Right));  
   };  
  
```  
  
#### Parámetros  
 `Type`, `Type1`, `Type2`  
 Cualquier tipo que admite un `operator&&` que toma operandos de los tipos especificados o deducidos.  
  
 `Left`  
 Operando izquierdo de la operación de conjunción lógica.  La plantilla no especializada toma un argumento de referencia de valor L de tipo `Type`.  La plantilla especializada realiza el reenvío directo de los argumentos de referencia de valor L y valor R del tipo deducido `Type1`.  
  
 `Right`  
 Operando derecho de la operación de conjunción lógica.  La plantilla no especializada toma un argumento de referencia de valor L de tipo `Type`.  La plantilla especializada realiza el reenvío directo de los argumentos de referencia de valor L y valor R del tipo deducido `Type2`.  
  
## Valor devuelto  
 Resultado de `Left` `&&` `Right`.  La plantilla especializada realiza el reenvío directo del resultado, que tiene el tipo devuelto por `operator&&`.  
  
## Comentarios  
 Para los tipos definidos por el usuario, no se realiza la evaluación cortocircuitada de los operandos.  `operator&&` evalúa ambos argumentos.  
  
## Ejemplo  
  
```  
// functional_logical_and.cpp  
// compile with: /EHsc  
  
#define _CRT_RAND_S  
#include <stdlib.h>  
#include <deque>  
#include <algorithm>  
#include <functional>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   deque<bool> d1, d2, d3( 7 );  
   deque<bool>::iterator iter1, iter2, iter3;  
  
   unsigned int randomValue;  
  
   int i;  
   for ( i = 0 ; i < 7 ; i++ )  
   {  
      if ( rand_s( &randomValue ) == 0 )  
      {  
         d1.push_back((bool)(( randomValue % 2 ) != 0));  
      }  
  
   }  
  
   int j;  
   for ( j = 0 ; j < 7 ; j++ )  
   {  
      if ( rand_s( &randomValue ) == 0 )  
      {  
         d2.push_back((bool)(( randomValue % 2 ) != 0));  
      }  
   }  
  
   cout << boolalpha;    // boolalpha I/O flag on  
  
   cout << "Original deque:\n d1 = ( " ;  
   for ( iter1 = d1.begin( ) ; iter1 != d1.end( ) ; iter1++ )  
      cout << *iter1 << " ";  
   cout << ")" << endl;  
  
   cout << "Original deque:\n d2 = ( " ;  
   for ( iter2 = d2.begin( ) ; iter2 != d2.end( ) ; iter2++ )  
      cout << *iter2 << " ";  
   cout << ")" << endl;  
  
   // To find element-wise conjunction of the truth values  
   // of d1 & d2, use the logical_and function object  
   transform( d1.begin( ), d1.end( ), d2.begin( ),  
      d3.begin( ), logical_and<bool>( ) );  
   cout << "The deque which is the conjuction of d1 & d2 is:\n d3 = ( " ;  
   for ( iter3 = d3.begin( ) ; iter3 != d3.end( ) ; iter3++ )  
      cout << *iter3 << " ";  
   cout << ")" << endl;  
}  
```  
  
  **Original deque:**  
 **d1 \= \( true true true true true false false \)**  
**Original deque:**  
 **d2 \= \( true false true true false true false \)**  
**The deque which is the conjuction of d1 & d2 is:**  
 **d3 \= \( true false true true false false false \)**   
## Requisitos  
 **Encabezado:** \<functional\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)