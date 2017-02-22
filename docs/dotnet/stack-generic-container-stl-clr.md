---
title: "stack::generic_container (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::stack::generic_container"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "generic_container (miembro) [STL/CLR]"
ms.assetid: 00f106c4-2a02-41cd-80de-f413c9355c74
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# stack::generic_container (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El tipo de interfaz genérica para el adaptador del contenedor.  
  
## Sintaxis  
  
```  
typedef Microsoft::VisualC::StlClr::IStack<Value>  
    generic_container;  
```  
  
## Comentarios  
 El tipo se describe la interfaz genérica para esta clase de adaptador de contenedor de plantilla.  
  
## Ejemplo  
  
```  
// cliext_stack_generic_container.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get interface to container   
    Mystack::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1->get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    gc1->push(L'd');   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify original and display generic   
    c1.push(L'e');   
    for each (wchar_t elem in gc1->get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **a b c**  
 **una c d b**  
 **una d e de la b c**   
## Requisitos  
 cliext \<\/pila de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 <xref:Microsoft.VisualC.StlClr.IStack%602>   
 [pila](../dotnet/stack-stl-clr.md)   
 [stack::generic\_value](../dotnet/stack-generic-value-stl-clr.md)