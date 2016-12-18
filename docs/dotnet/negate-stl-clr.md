---
title: "negate (STL/CLR) | Microsoft Docs"
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
  - "cliext::negate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "negate (función) [STL/CLR]"
ms.assetid: 58e4c339-0dee-4db8-b2cc-de8920977039
caps.latest.revision: 18
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# negate (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla describe un functor que, cuando se invoca, devuelva el argumento negado.  Se utiliza especifica un objeto de función en términos del tipo de argumento.  
  
## Sintaxis  
  
```  
template<typename Arg>  
    ref class negate  
    { // wrap operator()  
public:  
    typedef Arg argument_type;  
    typedef bool result_type;  
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<  
        argument_type, result_type>  
        delegate_type;  
  
    negate();  
    negate(negate<Arg>% right);  
  
    result_type operator()(argument_type left);  
    operator delegate_type^();  
    };  
```  
  
#### Parámetros  
 Argumento  
 El tipo de los argumentos.  
  
## Funciones miembro  
  
|Definición de tipo|Descripción|  
|------------------------|-----------------|  
|argument\_type|El tipo de argumento de functor.|  
|delegate\_type|El tipo de delegado genérico.|  
|result\_type|El tipo de resultado de functor.|  
  
|Miembro|Descripción|  
|-------------|-----------------|  
|negate|Construye el functor.|  
  
|operador ??|Descripción|  
|-----------------|-----------------|  
|operator\(\)|Calcula la función deseada.|  
|delegate\_type^ de operador|Convierte el functor un delegado.|  
  
## Comentarios  
 La clase de plantilla describe un functor de uno\- argumento.  Define el operador `operator()` de miembro para que, cuando el objeto se denomina como función, devuelva el argumento negado.  
  
 También puede pasar el objeto como argumento de la función cuyo tipo es `delegate_type^` y se convierte correctamente.  
  
## Ejemplo  
  
```  
// cliext_negate.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(-3);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 -3"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c3.begin(), cliext::negate<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **4 \-3**  
 **\-4 3**   
## Requisitos  
 cliext \<de**Encabezado:** \/funcional\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [logical\_not](../dotnet/logical-not-stl-clr.md)