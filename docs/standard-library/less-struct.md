---
title: "less (Struct) | Microsoft Docs"
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
  - "std::less"
  - "std.less"
  - "less"
  - "xfunctional/std::less"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "less (struct)"
  - "less (función)"
ms.assetid: 39349da3-11cd-4774-b2cc-b46af5aae5d7
caps.latest.revision: 24
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# less (Struct)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Predicado binario que realiza la operación menor que \(`operator<`\) sobre sus argumentos.  
  
## Sintaxis  
  
```  
template<class Type = void>  
   struct less : public binary_function <Type, Type, bool>   
   {  
      bool operator()(  
         const Type& Left,   
         const Type& Right  
      ) const;  
   };  
  
// specialized transparent functor for operator<  
template<>  
   struct less<void>  
   {  
      template<class Type1, class Type2>  
      auto operator()(Type1&& Left, Type2&& Right) const  
         -> decltype(std::forward<Type1>(Left)  
            < std::forward<Type2>(Right));  
   };  
  
```  
  
#### Parámetros  
 `Type`, `Type1`, `Type2`  
 Cualquier tipo que admite un `operator<` que toma operandos de los tipos especificados o deducidos.  
  
 `Left`  
 Operando izquierdo de la operación menor que.  La plantilla no especializada toma un argumento de referencia de valor L de tipo `Type`.  La plantilla especializada realiza el reenvío directo de los argumentos de referencia de valor L y valor R del tipo deducido `Type1`.  
  
 `Right`  
 Operando derecho de la operación menor que.  La plantilla no especializada toma un argumento de referencia de valor L de tipo `Type`.  La plantilla especializada realiza el reenvío directo de los argumentos de referencia de valor L y valor R del tipo deducido `Type2`.  
  
## Valor devuelto  
 Resultado de `Left` `<` `Right`.  La plantilla especializada realiza el reenvío directo del resultado, que tiene el tipo devuelto por `operator<`.  
  
## Comentarios  
 El predicado binario `less`\<`Type`\> proporciona una ordenación débil estricta de un conjunto de valores de elementos de tipo `Type` en clases de equivalencia, si y solo si este tipo satisface los requisitos matemáticos estándar para que se pueda ordenar de esa forma.  Las especializaciones para cualquier tipo de puntero producen una ordenación total de los elementos, en la que todos los elementos de valores distintos están ordenados unos con respecto a otros.  
  
## Ejemplo  
  
```  
// functional_less.cpp  
// compile with: /EHsc  
#include <vector>  
#include <algorithm>  
#include <functional>  
#include <iostream>  
  
struct MyStruct {  
   MyStruct(int i) : m_i(i){}  
  
   bool operator < (const MyStruct & rhs) const {  
      return m_i < rhs.m_i;  
   }     
  
   int m_i;  
};  
  
int main() {  
   using namespace std;  
   vector <MyStruct> v1;  
   vector <MyStruct>::iterator Iter1;  
   vector <MyStruct>::reverse_iterator rIter1;  
  
   int i;  
   for ( i = 0 ; i < 7 ; i++ )       
       v1.push_back( MyStruct(rand()));  
  
   cout << "Original vector v1 = ( " ;  
   for ( Iter1 = v1.begin() ; Iter1 != v1.end() ; Iter1++ )   
cout << Iter1->m_i << " ";  
   cout << ")" << endl;  
  
   // To sort in ascending order,  
   sort( v1.begin( ), v1.end( ), less<MyStruct>());  
  
   cout << "Sorted vector v1 = ( " ;  
   for ( Iter1 = v1.begin() ; Iter1 != v1.end() ; Iter1++ )   
cout << Iter1->m_i << " ";  
   cout << ")" << endl;  
 }  
```  
  
## Resultados  
  
```  
Original vector v1 = ( 41 18467 6334 26500 19169 15724 11478 )  
Sorted vector v1 = ( 41 6334 11478 15724 18467 19169 26500 )  
```  
  
## Requisitos  
 **Encabezado:** \<functional\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)