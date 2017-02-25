---
title: "binder2nd (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.binder2nd"
  - "binder2nd"
  - "xfunctional/std::binder2nd"
  - "std::binder2nd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "binder2nd (clase)"
ms.assetid: b2a9c1d1-dfc4-4ca9-a10e-ae84e195a62d
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# binder2nd (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Clase de plantilla que proporciona un constructor que convierte un objeto de función binaria en un objeto de función unaria enlazando el segundo argumento de la función binaria a un valor especificado.  
  
## Sintaxis  
  
```  
template<class Operation>  
   class binder2nd  
      : public unary_function <  
         typename Operation::first_argument_type,  
         typename Operation::result_type>   
   {  
   public:  
   typedef typename Operation::argument_type argument_type;  
   typedef typename Operation::result_type result_type;  
   binder2nd(  
      const Operation& _Func,  
      const typename Operation::second_argument_type& _Right  
   );  
   result_type operator()(  
      const argument_type& _Left  
   ) const;  
   result_type operator()(  
      argument_type& _Left  
   ) const;  
   protected:  
   Operation op;  
   typename Operation::second_argument_type value;  
   };  
```  
  
#### Parámetros  
 `_Func`  
 El objeto binario de función para convertirse en un objeto singular de la función.  
  
 `_Right`  
 El valor al que el segundo argumento del objeto binario de la función debe ser enlazado.  
  
 `_Left`  
 El valor del argumento que el objeto binario bien compara el valor fijo del segundo argumento.  
  
## Valor devuelto  
 El objeto singular de la función que resultados de enlace el segundo argumento del objeto binario de la función al valor `_Right.`  
  
## Comentarios  
 La clase de plantilla almacena una copia de un \_Func binario del objeto function en **op**, y una copia de `_Right` en **Valor**.  Define la función `operator()` miembro como devolver **op**\(`_Left`, **Valor**\).  
  
 Si `_Func` es un objeto de **Operación** tipo y c es una constante, entonces [bind2nd](../Topic/bind2nd%20Function.md) \( `_Func`, `c` \) es equivalente al constructor de clase `binder2nd`\<**Operación**\> \( `_Func`, `c` \) de `binder2nd` y más conveniente.  
  
## Ejemplo  
  
```  
// functional_binder2nd.cpp  
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
        binder2nd<greater<int> >(greater<int>(), 10));  
    cout << "The number of elements in v1 greater than 10 is: "  
         << result1 << "." << endl;  
  
    // Compare using binder1st fixing 1st argument:  
    // count the number of integers < 10 in the vector  
    vector<int>::iterator::difference_type result2;  
    result2 = count_if(v1.begin(), v1.end(),  
        binder1st<greater<int> >(greater<int>(), 10));  
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