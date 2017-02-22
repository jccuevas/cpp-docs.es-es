---
title: "binder1st (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "xfunctional/std::binder1st"
  - "std::binder1st"
  - "binder1st"
  - "std.binder1st"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "binder1st (clase)"
ms.assetid: 6b8ee343-c82f-48f8-867d-06f9d1d324c0
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# binder1st (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Clase de plantilla que proporciona un constructor que convierte un objeto de función binaria en un objeto de función unaria enlazando el primer argumento de la función binaria a un valor especificado.  
  
## Sintaxis  
  
```  
template<class Operation>  
class binder1st  
   : public unary_function <  
      typename Operation::second_argument_type,  
      typename Operation::result_type>   
  {  
   public:  
   typedef typename Operation::argument_type argument_type;  
   typedef typename Operation::result_type result_type;  
   binder1st(  
      const Operation & _Func,  
      const typename Operation::first_argument_type& _Left  
   );  
   result_type operator()(  
      const argument_type& _Right  
   ) const;  
   result_type operator()(  
      const argument_type& _Right  
   ) const;  
   protected:  
   Operation op;  
   typename Operation::first_argument_type value;  
   };  
```  
  
#### Parámetros  
 `_Func`  
 El objeto binario de función para convertirse en un objeto singular de la función.  
  
 `_Left`  
 El valor al que el primer argumento del objeto binario de la función debe ser enlazado.  
  
 `_Right`  
 El valor del argumento que el objeto binario bien compara el valor fijo del segundo argumento.  
  
## Valor devuelto  
 El objeto singular de la función que resultados de enlace el primer argumento del objeto binario de la función al valor `_Left.`  
  
## Comentarios  
 La clase de plantilla almacena una copia de un objeto binario `_Func` de la función en **op**, y una copia de `_Left` en **Valor**.  Define la función `operator()` miembro como devolver **op**\(**Valor**, `_Right`\).  
  
 Si `_Func` es un objeto de **Operación** escrito y `c` es una constante, entonces [bind1st](../Topic/bind1st%20Function.md) \( `_Func`, `c` \) es equivalente al constructor de clase `binder1st`\<**Operación**\> \( `_Func`, `c` \) de `binder1st` y más conveniente.  
  
## Ejemplo  
  
```  
// functional_binder1st.cpp  
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
    for (i = 0; i <= 5; i++)  
    {  
        v1.push_back(5 * i);  
    }  
  
    cout << "The vector v1 = ( ";  
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)  
        cout << *Iter << " ";  
    cout << ")" << endl;  
  
    // Count the number of integers > 10 in the vector  
    vector<int>::iterator::difference_type result1;  
    result1 = count_if(v1.begin(), v1.end(),  
        binder1st<less<int> >(less<int>(), 10));  
    cout << "The number of elements in v1 greater than 10 is: "  
         << result1 << "." << endl;  
  
    // Compare use of binder2nd fixing 2nd argument:  
    // count the number of integers < 10 in the vector  
    vector<int>::iterator::difference_type result2;  
    result2 = count_if(v1.begin(), v1.end(),  
        binder2nd<less<int> >(less<int>(), 10));  
    cout << "The number of elements in v1 less than 10 is: "  
         << result2 << "." << endl;  
}  
```  
  
  **The vector v1 \= \( 0 5 10 15 20 25 \)**  
**El número de elementos en v1 mayor de 10 es: 3.**  
**El número de elementos en v1 menos de 10 es: 2.**   
## Requisitos  
 **Encabezado:** \<functional\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)