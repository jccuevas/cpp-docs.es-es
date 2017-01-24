---
title: "logical_not (Struct) | Microsoft Docs"
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
  - "std.logical_not"
  - "logical_not"
  - "xfunctional/std::logical_not"
  - "std::logical_not"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "logical_not (clase)"
  - "logical_not (struct)"
ms.assetid: 892db678-31da-4540-974b-17b05efc0849
caps.latest.revision: 21
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# logical_not (Struct)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Objeto de función predefinido que realiza la operación not lógica \(`operator!`\) sobre su argumento.  
  
## Sintaxis  
  
```  
template<class Type = void>  
   struct logical_not : public unary_function<Type, bool>   
   {  
      bool operator()(  
         const Type& Left  
      ) const;  
   };  
  
// specialized transparent functor for operator!  
template<>  
   struct logical_not<void>  
   {  
      template<class Type>  
      auto operator()(Type&& Left) const  
         -> decltype(!std::forward<Type>(Left));  
   };  
  
```  
  
#### Parámetros  
 `Type`  
 Cualquier tipo que admite un `operator!` que toma un operando del tipo especificado o deducido.  
  
 `Left`  
 Operando de la operación not lógica.  La plantilla no especializada toma un argumento de referencia de valor L de tipo `Type`.  La plantilla especializada realiza el reenvío directo de los argumentos de referencia de valor L y valor R del tipo deducido `Type`.  
  
## Valor devuelto  
 Resultado de `!``Left`.  La plantilla especializada realiza el reenvío directo del resultado, que tiene el tipo devuelto por `operator!`.  
  
## Ejemplo  
  
```  
// functional_logical_not.cpp  
// compile with: /EHsc  
#include <deque>  
#include <algorithm>  
#include <functional>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   deque<bool> d1, d2 ( 7 );  
   deque<bool>::iterator iter1, iter2;  
  
   int i;  
   for ( i = 0 ; i < 7 ; i++ )  
   {  
      d1.push_back((bool)((i % 2) != 0));  
   }  
  
   cout << boolalpha;    // boolalpha I/O flag on  
  
   cout << "Original deque:\n d1 = ( " ;  
   for ( iter1 = d1.begin( ) ; iter1 != d1.end( ) ; iter1++ )  
      cout << *iter1 << " ";  
   cout << ")" << endl;  
  
   // To flip all the truth values of the elements,  
   // use the logical_not function object  
   transform( d1.begin( ), d1.end( ), d2.begin( ),logical_not<bool>( ) );  
   cout << "The deque with its values negated is:\n d2 = ( " ;  
   for ( iter2 = d2.begin( ) ; iter2 != d2.end( ) ; iter2++ )  
      cout << *iter2 << " ";  
   cout << ")" << endl;  
}  
```  
  
  **Original deque:**  
 **d1 \= \( false true false true false true false \)**  
**The deque with its values negated is:**  
 **d2 \= \( true false true false true false true \)**   
## Requisitos  
 **Encabezado:** \<functional\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)