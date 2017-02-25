---
title: "priority_queue::size_type (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::priority_queue::size_type"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "size_type (miembro) [STL/CLR]"
ms.assetid: 0f38e670-4f61-474a-990c-0b8cd31ada5e
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# priority_queue::size_type (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El tipo de una distancia firmados entre el elemento dos.  
  
## Sintaxis  
  
```  
typedef int size_type;  
```  
  
## Comentarios  
 El tipo describe un recuento negativo del elemento.  
  
## Ejemplo  
  
```  
// cliext_priority_queue_size_type.cpp   
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
  
// compute positive difference   
    Mypriority_queue::size_type diff = c1.size();   
    c1.pop();   
    c1.pop();   
    diff -= c1.size();   
    System::Console::WriteLine("size difference = {0}", diff);   
    return (0);   
    }  
  
```  
  
  **c a b**  
**difiere del tamaño \= 2**   
## Requisitos  
 cliext \<\/cola de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [priority\_queue](../dotnet/priority-queue-stl-clr.md)   
 [priority\_queue::empty](../dotnet/priority-queue-empty-stl-clr.md)