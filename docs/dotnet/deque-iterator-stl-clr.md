---
title: "deque::iterator (STL/CLR) | Microsoft Docs"
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
  - "cliext::deque::iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "iterator (miembro) [STL/CLR]"
ms.assetid: 3529e793-5d56-4cb2-898d-fdedb90b5c0c
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# deque::iterator (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El tipo de un iterador para la secuencia controlada.  
  
## Sintaxis  
  
```  
typedef T1 iterator;  
```  
  
## Comentarios  
 El tipo describe un objeto de tipo sin especificar `T1` que sirva como iterador de acceso aleatorio para la secuencia controlada.  
  
## Ejemplo  
  
```  
// cliext_deque_iterator.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    cliext::deque<wchar_t>::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
  
// alter first element and redisplay   
    it = c1.begin();   
    *it = L'x';   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **b c x**   
## Requisitos  
 **Encabezado:** \<cliext\/deque\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [deque](../dotnet/deque-stl-clr.md)   
 [deque::const\_iterator](../dotnet/deque-const-iterator-stl-clr.md)