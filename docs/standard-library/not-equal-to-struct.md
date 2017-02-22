---
title: "not_equal_to (Struct) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.not_equal_to"
  - "std::not_equal_to"
  - "not_equal_to"
  - "xfunctional/std::not_equal_to"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "not_equal_to (función)"
  - "not_equal_to (struct)"
ms.assetid: 333fce09-4f51-44e0-ba26-533bccffd485
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# not_equal_to (Struct)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Predicado binario que realiza la operación de desigualdad \(`operator!=`\) sobre sus argumentos.  
  
## Sintaxis  
  
```  
template<class Type = void>  
   struct not_equal_to : public binary_function<Type, Type, bool>   
   {  
      bool operator()(  
         const Type& Left,   
         const Type& Right  
      ) const;  
   };  
  
// specialized transparent functor for operator!=  
template<>  
   struct not_equal_to<void>  
   {  
      template<class Type1, class Type2>  
      auto operator()(Type1&& Left, Type2&& Right) const  
      -> decltype(std::forward<Type1>(Left)  
         != std::forward<Type2>(Right));  
   };  
  
```  
  
#### Parámetros  
 `Type`, `Type1`, `Type2`  
 Cualquier tipo que admite un `operator!=` que toma operandos de los tipos especificados o deducidos.  
  
 `Left`  
 Operando izquierdo de la operación de desigualdad.  La plantilla no especializada toma un argumento de referencia de valor L de tipo `Type`.  La plantilla especializada realiza el reenvío directo de los argumentos de referencia de valor L y valor R del tipo deducido `Type1`.  
  
 `Right`  
 Operando derecho de la operación de desigualdad.  La plantilla no especializada toma un argumento de referencia de valor L de tipo `Type`.  La plantilla especializada realiza el reenvío directo de los argumentos de referencia de valor L y valor R del tipo deducido `Type2`.  
  
## Valor devuelto  
 Resultado de `Left` `!=` `Right`.  La plantilla especializada realiza el reenvío directo del resultado, que tiene el tipo devuelto por `operator!=`.  
  
## Comentarios  
 Los objetos de tipo `Type` deben ser comparables en igualdad.  Esto requiere que el `operator!=` definido en el conjunto de objetos satisfaga las propiedades matemáticas de una relación de equivalencia.  Todos los tipos numéricos y de puntero integrados cumplen este requisito.  
  
## Ejemplo  
  
```  
// functional_not_equal_to.cpp  
// compile with: /EHsc  
#include <vector>  
#include <functional>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
int main( )  
{  
   vector <double> v1, v2, v3 (6);  
   vector <double>::iterator Iter1, Iter2, Iter3;  
  
   int i;  
   for ( i = 0 ; i <= 5 ; i+=2 )  
   {  
      v1.push_back( 2.0 *i );  
      v1.push_back( 2.0 * i + 1.0 );  
   }  
  
   int j;  
   for ( j = 0 ; j <= 5 ; j+=2 )  
   {  
      v2.push_back( - 2.0 * j );  
      v2.push_back( 2.0 * j + 1.0 );  
   }  
  
   cout << "The vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   cout << "The vector v2 = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")" << endl;  
  
   // Testing for the element-wise equality between v1 & v2  
   transform ( v1.begin( ), v1.end( ), v2.begin( ), v3.begin ( ),   
      not_equal_to<double>( ) );  
  
   cout << "The result of the element-wise not_equal_to comparsion\n"  
      << "between v1 & v2 is: ( " ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )  
      cout << *Iter3 << " ";  
   cout << ")" << endl;  
}  
```  
  
  **The vector v1 \= \( 0 1 4 5 8 9 \)**  
**The vector v2 \= \( \-0 1 \-4 5 \-8 9 \)**  
**The result of the element\-wise not\_equal\_to comparsion**  
**between v1 & v2 is: \( 0 0 1 0 1 0 \)**   
## Requisitos  
 **Encabezado:** \<functional\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)