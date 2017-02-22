---
title: "iterator_traits (Struct) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::iterator_traits"
  - "xutility/std::iterator_traits"
  - "iterator_traits"
  - "std.iterator_traits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "iterator_traits (clase)"
  - "iterator_traits (struct)"
ms.assetid: 8b92c2c5-f658-402f-8ca1-e7ae301b8514
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# iterator_traits (Struct)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Struct auxiliares de la plantilla se utiliza para especificar todas las definiciones de tipo críticas que un iterador debe tener.  
  
## Sintaxis  
  
```  
template<class Iterator>  
    struct iterator_traits {  
        typedef typename Iterator::iterator_category iterator_category;  
        typedef typename Iterator::value_type value_type;  
        typedef typename Iterator::difference_type difference_type;  
        typedef difference_type distance_type;  
        typedef typename Iterator::pointer pointer;  
        typedef typename Iterator::reference reference;  
    };  
template<class Type>  
    struct iterator_traits<Type*> {  
        typedef random_access_iterator_tag iterator_category;  
        typedef Type value_type;  
        typedef ptrdiff_t difference_type;  
        typedef difference_type distance_type;  
        typedef Type *pointer;  
        typedef Type& reference;  
    };  
template<class Type>  
    struct iterator_traits<const Type*> {  
        typedef random_access_iterator_tag iterator_category;  
        typedef Type value_type;  
        typedef ptrdiff_t difference_type;  
        typedef difference_type distance_type;  
        typedef const Type *pointer;  
        typedef const Type& reference;  
    };  
```  
  
## Comentarios  
 Struct de plantilla define los tipos de miembro  
  
-   **iterator\_category**: un sinónimo de **Iterator::iterator\_category**.  
  
-   `value_type`: un sinónimo de **Iterator::value\_type**.  
  
-   `difference_type`: un sinónimo de **Iterator::difference\_type**.  
  
-   `distance_type`: un sinónimo de **Iterator::difference\_type.**  
  
-   **puntero**: un sinónimo de **Iterator::pointer**.  
  
-   **reference**: un sinónimo de **Iterator::reference**.  
  
 Especializaciones parciales determinan los tipos críticos asociados a un puntero de objeto de **Type \*** tipo o const **Type \***.  
  
 En esta implementación puede utilizar varias funciones de plantilla que no hacen uso de especialización parcial:  
  
```  
template<class Category, class Type, class Diff>  
C _Iter_cat(const iterator<Category, Ty, Diff>&);  
template<class Ty>  
    random_access_iterator_tag _Iter_cat(const Ty *);  
  
template<class Category, class Ty, class Diff>  
Ty *_Val_type(const iterator<Category, Ty, Diff>&);  
template<class Ty>  
    Ty *_Val_type(const Ty *);  
  
template<class Category, class Ty, class Diff>  
Diff *_Dist_type(const iterator<Category, Ty, Diff>&);  
template<class Ty>  
    ptrdiff_t *_Dist_type(const Ty *);  
```  
  
 qué determinan a varios de los mismos tipos más indirectamente.  Utilice estas funciones como argumentos en una llamada de función.  Su único propósito es proporcionar un parámetro de tipo de plantilla útil a la función llamada.  
  
## Ejemplo  
  
```  
// iterator_traits.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <iterator>  
#include <vector>  
#include <list>  
  
using namespace std;  
  
template< class it >  
void  
function( it i1, it i2 )  
{  
   iterator_traits<it>::iterator_category cat;  
   cout << typeid( cat ).name( ) << endl;  
   while ( i1 != i2 )  
   {  
      iterator_traits<it>::value_type x;  
      x = *i1;  
      cout << x << " ";  
      i1++;  
   };     
   cout << endl;  
};  
  
int main( )   
{  
   vector<char> vc( 10,'a' );  
   list<int> li( 10 );  
   function( vc.begin( ), vc.end( ) );  
   function( li.begin( ), li.end( ) );  
}  
```  
  
  **std::random\_access\_iterator\_tag struct**  
**a**   
**std::bidirectional\_iterator\_tag struct**  
**0 0 0 0 0 0 0 0 0 0**    
## Requisitos  
 **Encabezado:** \<iterator\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<iterator\>](../standard-library/iterator.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)