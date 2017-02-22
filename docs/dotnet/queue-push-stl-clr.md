---
title: "queue::push (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::queue::push"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "push (miembro) [STL/CLR]"
ms.assetid: 97cf1f98-d4c4-417f-b57a-89cdd351ef65
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# queue::push (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Agrega un nuevo elemento pasado.  
  
## Sintaxis  
  
```  
void push(value_type val);  
```  
  
## Comentarios  
 La función miembro agrega un elemento con el valor `val` al final de la cola.  Se utiliza para anexar un elemento a la cola.  
  
## Ejemplo  
  
```  
// cliext_queue_push.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**   
## Requisitos  
 cliext \<\/cola de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [queue](../dotnet/queue-stl-clr.md)   
 [queue::pop](../dotnet/queue-pop-stl-clr.md)