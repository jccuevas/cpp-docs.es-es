---
title: "bind2nd (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::bind2nd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bind2nd (función) [STL/CLR]"
ms.assetid: 457cebea-38e4-4466-a468-fe9eb138e80c
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# bind2nd (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Genera `binder2nd` para un argumento y un functor.  
  
## Sintaxis  
  
```  
template<typename Fun,  
    typename Arg>  
    binder2nd<Fun> bind2nd(Fun% functor,  
        Arg right);  
```  
  
## Parámetros de plantilla  
 Argumento  
 Tipo del argumento.  
  
 Debería  
 El tipo de functor.  
  
## Parámetros de función  
 functor  
 El functor a ajustar.  
  
 right  
 El segundo argumento de ajustar.  
  
## Comentarios  
 La función de la plantilla devuelve [binder2nd](../dotnet/binder2nd-stl-clr.md)`<Fun>(functor, right)`.  Se utiliza como una manera cómoda de ajustar un functor de dos\- argumento y el segundo argumento en un functor de uno\- argumento que lo llame con un primer argumento.  
  
## Ejemplo  
  
```  
// cliext_bind2nd.cpp   
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
    cliext::binder2nd<cliext::minus<int> > sub4(sub_op, 4);   
  
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        sub4);   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display with function   
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),   
        bind2nd(sub_op, 4));   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **4 3**  
 **0 \-1**  
 **0 \-1**   
## Requisitos  
 cliext \<de**Encabezado:** \/funcional\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [binder2nd](../dotnet/binder2nd-stl-clr.md)