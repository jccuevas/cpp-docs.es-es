---
title: "deque::pop_back (STL/CLR) | Microsoft Docs"
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
  - "cliext::deque::pop_back"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "pop_back (miembro) [STL/CLR]"
ms.assetid: 528d2c89-104c-45f7-8f05-41fe217ee37c
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# deque::pop_back (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Quita el último elemento.  
  
## Sintaxis  
  
```  
void pop_back();  
```  
  
## Comentarios  
 La función miembro quita el último elemento de la secuencia controlada, que no puede estar vacía.  Se utiliza para acortar el deque por un elemento en la reproducción.  
  
## Ejemplo  
  
```  
// cliext_deque_pop_back.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// pop an element and redisplay   
    c1.pop_back();   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **una b**   
## Requisitos  
 **Encabezado:** \<cliext\/deque\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [deque](../dotnet/deque-stl-clr.md)   
 [deque::pop\_front](../dotnet/deque-pop-front-stl-clr.md)   
 [deque::push\_back](../dotnet/deque-push-back-stl-clr.md)   
 [deque::push\_front](../dotnet/deque-push-front-stl-clr.md)