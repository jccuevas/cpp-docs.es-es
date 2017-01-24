---
title: "stack::value_type (STL/CLR) | Microsoft Docs"
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
  - "cliext::stack::value_type"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "value_type (miembro) [STL/CLR]"
ms.assetid: 867ff1a7-c91c-4168-9b85-21fd0dcf4806
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# stack::value_type (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El tipo de un elemento.  
  
## Sintaxis  
  
```  
typedef Value value_type;  
```  
  
## Comentarios  
 El tipo es un sinónimo para el parámetro `Value`de la plantilla.  
  
## Ejemplo  
  
```  
// cliext_stack_value_type.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display reversed contents " a b c" using value_type   
    for (; !c1.empty(); c1.pop())   
        {   // store element in value_type object   
        Mystack::value_type val = c1.top();   
  
        System::Console::Write(" {0}", val);   
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
 [stack::const\_reference](../dotnet/stack-const-reference-stl-clr.md)   
 [stack::reference](../dotnet/stack-reference-stl-clr.md)