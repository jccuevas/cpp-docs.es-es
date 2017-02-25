---
title: "stack::const_reference (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::stack::const_reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "const_reference (miembro) [STL/CLR]"
ms.assetid: 36be8e21-f2b8-4c2e-a00e-276e73f0d802
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# stack::const_reference (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El tipo de una referencia constante a un elemento.  
  
## Sintaxis  
  
```  
typedef value_type% const_reference;  
```  
  
## Comentarios  
 El tipo describe una referencia constante a un elemento.  
  
## Ejemplo  
  
```  
// cliext_stack_const_reference.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display reversed contents " c b a"   
    for (; !c1.empty(); c1.pop())   
        {   // get a const reference to an element   
        Mystack::const_reference cref = c1.top();   
        System::Console::Write(" {0}", cref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **b a c**   
## Requisitos  
 cliext \<\/pila de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [pila](../dotnet/stack-stl-clr.md)   
 [stack::reference](../dotnet/stack-reference-stl-clr.md)   
 [stack::value\_type](../dotnet/stack-value-type-stl-clr.md)