---
title: "unary_negate (Clase) | Microsoft Docs"
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
  - "unary_negate"
  - "std::unary_negate"
  - "std.unary_negate"
  - "xfunctional/std::unary_negate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unary_negate (clase)"
ms.assetid: e3b86eec-3205-49b9-ab83-f55225af4e0c
caps.latest.revision: 21
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# unary_negate (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Clase de plantilla que proporciona una función miembro que niega el valor devuelto de una función unaria especificada.  
  
## Sintaxis  
  
```  
  
   template<class Predicate>  
class unary_negate  
   : public unary_function<  
      typename Predicate::argument_type,  
      bool>   
{  
public:  
explicit unary_negate(  
   const Predicate& _Func  
);  
bool operator()(  
   const typename Predicate::argument_type& _Left ) const;  
};  
```  
  
#### Parámetros  
 `_Func`  
 La función unario que se negará.  
  
 `_Left`  
 El operando de la función unario que se negará.  
  
## Valor devuelto  
 La negación de la función singular.  
  
## Comentarios  
 La clase de plantilla almacena una copia de un \_Func unario de objeto function.Define la función `operator()` miembro como devolver el \_Func de \#\#\#\!*\(\_Left\).*  
  
 El constructor de `unary_negate` raramente se utiliza directamente.  La función [not1](../Topic/not1%20Function.md) auxiliar proporciona una manera más fácil de declarar y utilizar el predicado del adaptador de **unary\_negator** .  
  
## Ejemplo  
  
```  
// functional_unary_negate.cpp  
// compile with: /EHsc  
#include <vector>  
#include <functional>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
int main()  
{  
    vector<int> v1;  
    vector<int>::iterator Iter;  
  
    int i;  
    for (i = 0; i <= 7; i++)  
    {  
        v1.push_back(5 * i);  
    }  
  
    cout << "The vector v1 = ( ";  
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)  
        cout << *Iter << " ";  
    cout << ")" << endl;  
  
    vector<int>::iterator::difference_type result1;  
    // Count the elements greater than 10  
    result1 = count_if(v1.begin(), v1.end(), bind2nd(greater<int>(), 10));  
    cout << "The number of elements in v1 greater than 10 is: "  
         << result1 << "." << endl;  
  
    vector<int>::iterator::difference_type result2;  
    // Use the negator to count the elements less than or equal to 10  
    result2 = count_if(v1.begin(), v1.end(),  
        unary_negate<binder2nd <greater<int> > >(bind2nd(greater<int>(),10)));  
  
    // The following helper function not1 also works for the above line  
    // not1(bind2nd(greater<int>(), 10)));  
  
    cout << "The number of elements in v1 not greater than 10 is: "  
         << result2 << "." << endl;  
}  
```  
  
  **El vector v1 \= \(0 5 10 15 20 25 30 35\)**  
**El número de elementos en v1 mayor de 10 es: 5.**  
**El número de elementos en v1 no mayor que 10 es: 3.**   
## Requisitos  
 **Encabezado:** \<functional\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)