---
title: "priority_queue::reference (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::priority_queue::reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "miembro de referencia [STL/CLR]"
ms.assetid: b063eaf1-c238-4aef-ac54-a81d0f671418
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# priority_queue::reference (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El tipo de una referencia a un elemento.  
  
## Sintaxis  
  
```  
typedef value_type% reference;  
```  
  
## Comentarios  
 El tipo describe una referencia a un elemento.  
  
## Ejemplo  
  
```  
// cliext_priority_queue_reference.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify top of priority_queue and redisplay   
    Mypriority_queue::reference ref = c1.top();   
    ref = L'x';   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **c a b**  
 **x a b**   
## Requisitos  
 cliext \<\/cola de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [priority\_queue](../dotnet/priority-queue-stl-clr.md)   
 [priority\_queue::const\_reference](../dotnet/priority-queue-const-reference-stl-clr.md)   
 [priority\_queue::value\_type](../dotnet/priority-queue-value-type-stl-clr.md)