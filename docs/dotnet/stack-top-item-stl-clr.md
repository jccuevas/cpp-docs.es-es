---
title: "stack::top_item (STL/CLR) | Microsoft Docs"
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
  - "cliext::stack::top_item"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "top_item (miembro) [STL/CLR]"
ms.assetid: 01571acf-4880-44c4-80c4-bd91408a032d
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# stack::top_item (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Tiene acceso al último elemento.  
  
## Sintaxis  
  
```  
property value_type top_item;  
```  
  
## Comentarios  
 La propiedad tiene acceso al último elemento de la secuencia controlada, que no puede estar vacía.  Se utiliza para leer o escribir el último elemento, cuando lo conoce existe.  
  
## Ejemplo  
  
```  
// cliext_stack_top_item.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("top_item = {0}", c1.top_item);   
  
// alter last item and reinspect   
    c1.top_item = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
**top\_item \= c**  
 **una b x**   
## Requisitos  
 cliext \<\/pila de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [pila](../dotnet/stack-stl-clr.md)   
 [stack::top](../dotnet/stack-top-stl-clr.md)