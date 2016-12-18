---
title: "binder1st (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::binder1st"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "binder1st (función) [STL/CLR]"
ms.assetid: a989c9cc-a485-45d9-bd19-519018e6974b
caps.latest.revision: 18
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# binder1st (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla describe un functor de uno\- argumento que, cuando se invoca, devuelva el functor almacenado de dos\- argumento con su primer argumento almacenado y el segundo argumento proporcionado.  Se utiliza especifica un objeto de función en términos de su functor almacenado.  
  
## Sintaxis  
  
```  
template<typename Fun>  
    ref class binder1st  
    { // wrap operator()  
public:  
    typedef Fun stored_function_type;  
    typedef typename Fun::first_argument_type first_argument_type;  
    typedef typename Fun::second_argument_type second_argument_type;  
    typedef typename Fun:result_type result_type;  
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<  
        second_argument_type, result_type>  
        delegate_type;  
  
    binder1st(Fun% functor, first_argument_type left);  
    binder1st(binder1st<Arg>% right);  
  
    result_type operator()(second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### Parámetros  
 Debería  
 El tipo de functor almacenado.  
  
## Funciones miembro  
  
|Definición de tipo|Descripción|  
|------------------------|-----------------|  
|delegate\_type|El tipo de delegado genérico.|  
|first\_argument\_type|El tipo del primer argumento de functor.|  
|result\_type|El tipo de resultado de functor.|  
|second\_argument\_type|El tipo de argumento de functor segundo.|  
|stored\_function\_type|El tipo de functor.|  
  
|Miembro|Descripción|  
|-------------|-----------------|  
|binder1st|Construye el functor.|  
  
|operador ??|Descripción|  
|-----------------|-----------------|  
|operator\(\)|Calcula la función deseada.|  
|operador delegate\_type^\(\)|Convierte el functor un delegado.|  
  
## Comentarios  
 La clase de plantilla describe un functor de uno\- argumento que almacena un functor de dos\- argumento y un primer argumento.  Define el operador `operator()` de miembro para que, cuando el objeto se denomina como función, devuelve el resultado de llamar al functor almacenado con el primer argumento almacenado y el segundo argumento proporcionado.  
  
 También puede pasar el objeto como argumento de la función cuyo tipo es `delegate_type^` y se convierte correctamente.  
  
## Ejemplo  
  
```  
// cliext_binder1st.cpp   
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
    Myvector c3(2, 0);   
  
// display initial contents " 4 3"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::minus<int> sub_op;   
    cliext::binder1st<cliext::minus<int> > subfrom3(sub_op, 3);   
  
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        subfrom3);   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        bind1st(sub_op, 3));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **4 3**  
 **\-1 0**  
 **\-1 0**   
## Requisitos  
 cliext \<de**Encabezado:** \/funcional\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [bind1st](../dotnet/bind1st-stl-clr.md)