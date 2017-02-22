---
title: "binary_negate (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "xfunctional/std::binary_negate"
  - "std::binary_negate"
  - "binary_negate"
  - "std.binary_negate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "binary_negate (clase)"
ms.assetid: 7b86f02c-af7e-4c7f-9df1-08addae4dd65
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# binary_negate (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Clase de plantilla que proporciona una función miembro que niega el valor devuelto de una función binaria especificada.  
  
## Sintaxis  
  
```  
  
   template<class Operation>  
class binary_negate  
   : public binary_function <  
      typename Operation::first_argument_type,  
      typename Operation::second_argument_type,   
      bool>   
{  
public:  
explicit binary_negate(  
   const Operation& _Func  
);  
bool operator()(  
   const typename Operation::first_argument_type& _Left,  
   const typename Operation::second_argument_type& _Right  
) const;  
};  
```  
  
#### Parámetros  
 `_Func`  
 La función binaria que se negará.  
  
 `_Left`  
 El operando izquierdo de la función binaria que se negará.  
  
 `_Right`  
 El operando derecho de la función binaria que se negará.  
  
## Valor devuelto  
 La negación de la función binaria.  
  
## Comentarios  
 La clase de plantilla almacena una copia de un \_Func binario del objeto function.  Define la función `operator()` miembro como devolver el \_Func de \#\#\#\!*\(\_Left, \_Right\).*  
  
 El constructor de `binary_negate` raramente se utiliza directamente.  La función [not2](../Topic/not2%20Function.md) auxiliar normalmente es preferible usar para declarar y utilizar el predicado del adaptador de **binary\_negator** .  
  
## Ejemplo  
  
```  
// functional_binary_negate.cpp  
// compile with: /EHsc  
#define _CRT_RAND_S  
#include <stdlib.h>  
  
#include <vector>  
#include <algorithm>  
#include <functional>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   vector <unsigned int> v1;  
   vector <unsigned int>::iterator Iter1;  
  
   unsigned int i;  
   v1.push_back( 6262 );  
   v1.push_back( 6262 );  
   unsigned int randVal = 0;  
   for ( i = 0 ; i < 5 ; i++ )  
   {  
      rand_s(&randVal);  
      v1.push_back( randVal );  
   }  
  
   cout << "Original vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // To sort in ascending order,  
   // use default binary predicate less<unsigned int>( )  
   sort( v1.begin( ), v1.end( ) );  
   cout << "Sorted vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   // To sort in descending order,  
   // use the binary_negate function  
   sort( v1.begin( ), v1.end( ),  
   binary_negate<less<unsigned int> >(less<unsigned int>( ) ) );  
  
   // The helper function not2 could also have been used  
   // in the above line and is usually preferred for convenience  
   // sort( v1.begin( ), v1.end( ), not2(less<unsigned int>( ) ) );  
  
   cout << "Resorted vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
}  
```  
  
  **Vector original v1 \= \(6262 6262 2233879413 2621500314 580942933 3715465425 3739828298\)**  
**Vector ordenados v1 \= \(6262 6262 580942933 2233879413 2621500314 3715465425 3739828298\)**  
**Vector recurrido v1 \= \(3739828298 3715465425 2621500314 2233879413 580942933 6262 6262\)**   
## Requisitos  
 **Encabezado:** \<functional\>  
  
 std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)