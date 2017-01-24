---
title: "bind1st (STL/CLR) | Microsoft Docs"
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
  - "cliext::bind1st"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bind1st (función) [STL/CLR]"
ms.assetid: 03a04cef-60fb-4667-b22a-22a387adb028
caps.latest.revision: 14
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# bind1st (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Genera `binder1st` para un argumento y un functor.  
  
## Sintaxis  
  
```  
template<typename Fun,  
    typename Arg>  
    binder1st<Fun> bind1st(Fun% functor,  
        Arg left);  
```  
  
## Parámetros de plantilla  
 Argumento  
 Tipo del argumento.  
  
 Debería  
 El tipo de functor.  
  
## Parámetros de función  
 functor  
 El functor a ajustar.  
  
 left  
 El primer argumento a ajustar.  
  
## Comentarios  
 La función de la plantilla devuelve [binder1st](../dotnet/binder1st-stl-clr.md)`<Fun>(functor, left)`.  Se utiliza como una manera cómoda de ajustar un functor de dos\- argumento y su primer argumento en un functor de uno\- argumento que lo llame con un segundo argumento.  
  
## Ejemplo  
  
```  
// cliext_bind1st.cpp   
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
 [binder1st](../dotnet/binder1st-stl-clr.md)