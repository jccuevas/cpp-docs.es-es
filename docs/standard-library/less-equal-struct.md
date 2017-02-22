---
title: "less_equal (Struct) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::less_equal"
  - "xfunctional/std::less_equal"
  - "std.less_equal"
  - "less_equal"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "less_equal (función)"
  - "less_equal (struct)"
ms.assetid: 32085782-c7e0-4310-9b40-8aa3c1bff211
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# less_equal (Struct)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Predicado binario que realiza la operación menor o igual que \(`operator<=`\) sobre sus argumentos.  
  
## Sintaxis  
  
```  
template<class Type = void>  
   struct less_equal : public binary_function <Type, Type, bool>   
   {  
      bool operator()(  
         const Type& Left,   
         const Type& Right  
      ) const;  
   };  
  
// specialized transparent functor for operator<=  
template<>  
   struct less_equal<void>  
   {  
      template<class Type1, class Type2>  
      auto operator()(Type1&& Left, Type2&& Right) const  
         -> decltype(std::forward<Type1>(Left)  
            <= std::forward<Type2>(Right));  
   };  
  
```  
  
#### Parámetros  
 `Type`, `Type1`, `Type2`  
 Cualquier tipo que admite un `operator<=` que toma operandos de los tipos especificados o deducidos.  
  
 `Left`  
 Operando izquierdo de la operación menor o igual que.  La plantilla no especializada toma un argumento de referencia de valor L de tipo `Type`.  La plantilla especializada realiza el reenvío directo de los argumentos de referencia de valor L y valor R del tipo deducido `Type1`.  
  
 `Right`  
 Operando derecho de la operación menor o igual que.  La plantilla no especializada toma un argumento de referencia de valor L de tipo `Type`.  La plantilla especializada realiza el reenvío directo de los argumentos de referencia de valor L y valor R del tipo deducido `Type2`.  
  
## Valor devuelto  
 Resultado de `Left` `<=` `Right`.  La plantilla especializada realiza el reenvío directo del resultado, que tiene el tipo devuelto por `operator<=`.  
  
## Comentarios  
 El predicado binario `less_equal`\<`Type`\> proporciona una ordenación débil estricta de un conjunto de valores de elementos de tipo `Type` en clases de equivalencia, si y solo si este tipo satisface los requisitos matemáticos estándar para que se pueda ordenar de esa forma.  Las especializaciones para cualquier tipo de puntero producen una ordenación total de los elementos, en la que todos los elementos de valores distintos están ordenados unos con respecto a otros.  
  
## Ejemplo  
  
```  
// functional_less_equal.cpp  
// compile with: /EHsc  
#define _CRT_RAND_S  
#include <stdlib.h>  
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
   vector <int>::reverse_iterator rIter1;  
   unsigned int randomNumber;  
  
   int i;  
   for ( i = 0 ; i < 5 ; i++ )  
   {  
      if ( rand_s( &randomNumber ) == 0 )  
      {  
         // Convert the random number to be between 1 - 50000  
         // This is done for readability purposes  
         randomNumber = ( unsigned int) ((double)randomNumber /   
            (double) UINT_MAX * 50000) + 1;  
  
         v1.push_back( randomNumber );  
      }  
   }  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      v1.push_back( 2836 );  
   }  
  
   cout << "Original vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // To sort in ascending order,  
   // use the binary predicate less_equal<int>( )  
   sort( v1.begin( ), v1.end( ), less_equal<int>( ) );  
   cout << "Sorted vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
}  
```  
  
## Resultados del ejemplo  
  
```  
Original vector v1 = ( 31247 37154 48755 15251 6205 2836 2836 2836 )  
Sorted vector v1 = ( 2836 2836 2836 6205 15251 31247 37154 48755 )  
```  
  
## Requisitos  
 **Encabezado:** \<functional\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)