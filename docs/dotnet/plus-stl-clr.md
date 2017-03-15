---
title: "plus (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::plus"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "plus (función) [STL/CLR]"
ms.assetid: 7ec8228a-72c7-4e47-9e63-23525d4a5416
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# plus (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla describe un functor que, cuando se invoca, devuelve el primer argumento más el segundo.  Se utiliza especifica un objeto de función en términos del tipo de argumento.  
  
## Sintaxis  
  
```  
template<typename Arg>  
    ref class plus  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef Arg result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    plus();  
    plus(plus<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### Parámetros  
 Argumento  
 El tipo de los argumentos y el valor devuelto.  
  
## Funciones miembro  
  
|Definición de tipo|Descripción|  
|------------------------|-----------------|  
|delegate\_type|El tipo de delegado genérico.|  
|first\_argument\_type|El tipo del primer argumento de functor.|  
|result\_type|El tipo de resultado de functor.|  
|second\_argument\_type|El tipo de argumento de functor segundo.|  
  
|Miembro|Descripción|  
|-------------|-----------------|  
|plus|Construye el functor.|  
  
|operador ??|Descripción|  
|-----------------|-----------------|  
|operator\(\)|Calcula la función deseada.|  
|delegate\_type^ de operador|Convierte el functor un delegado.|  
  
## Comentarios  
 La clase de plantilla describe un functor de dos\- argumento.  Define el operador `operator()` de miembro para que, cuando el objeto se denomina como función, devuelve el primer argumento más el segundo.  
  
 También puede pasar el objeto como argumento de la función cuyo tipo es `delegate_type^` y se convierte correctamente.  
  
## Ejemplo  
  
```  
// cliext_plus.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c2;   
    c2.push_back(2);   
    c2.push_back(1);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 2 1"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::plus<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **4 3**  
 **2 1**  
 **6 4**   
## Requisitos  
 cliext \<de**Encabezado:** \/funcional\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [minus](../dotnet/minus-stl-clr.md)