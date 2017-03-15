---
title: "deque::end (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::deque::end"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "end (miembro) [STL/CLR]"
ms.assetid: 3de3e816-3334-4b39-97ad-6f8771e9b4e9
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# deque::end (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Designa el final de la secuencia controlada.  
  
## Sintaxis  
  
```  
iterator end();  
```  
  
## Comentarios  
 La función miembro devuelve un iterador de acceso aleatorio que señala simplemente más allá del final de la secuencia controlada.  Se usa para obtener un iterador que designe el final de la secuencia controlada, indicado por `current`, pero su estado puede cambiar si cambia la longitud de la secuencia controlada.  
  
## Ejemplo  
  
```  
// cliext_deque_end.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last two items   
    cliext::deque<wchar_t>::iterator it = c1.end();   
    --it;   
    System::Console::WriteLine("*-- --end() = {0}", *--it);   
    System::Console::WriteLine("*--end() = {0}", *++it);   
  
// alter first two items and reinspect   
    *--it = L'x';   
    *++it = L'y';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
**\*\-\- \-\-end\(\) \= b**  
**\*\-\-end\(\) \= c**  
 **una y de x**   
## Requisitos  
 **Encabezado:** \<cliext\/deque\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [deque](../dotnet/deque-stl-clr.md)   
 [deque::back](../dotnet/deque-back-stl-clr.md)   
 [deque::back\_item](../dotnet/deque-back-item-stl-clr.md)   
 [deque::begin](../dotnet/deque-begin-stl-clr.md)