---
title: "multimap::end (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::multimap::end"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "end (miembro) [STL/CLR]"
ms.assetid: 8d3f9347-794d-4bd3-9bd1-50534fcf4ffe
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# multimap::end (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Designa el final de la secuencia controlada.  
  
## Sintaxis  
  
```  
iterator end();  
```  
  
## Comentarios  
 La función miembro devuelve un iterador bidireccional que señala simplemente más allá del final de la secuencia controlada.  Se usa para obtener un iterador que señala el final de la secuencia controlada; el cambio de doesn de estado no si la longitud de los cambios en los elementos de la secuencia.  
  
## Ejemplo  
  
```  
// cliext_multimap_end.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::multimap<wchar_t, int> Mymultimap;   
int main()   
    {   
    Mymultimap c1;   
    c1.insert(Mymultimap::make_value(L'a', 1));   
    c1.insert(Mymultimap::make_value(L'b', 2));   
    c1.insert(Mymultimap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymultimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// inspect last two items   
    Mymultimap::iterator it = c1.end();   
    --it;   
    --it;   
    System::Console::WriteLine("*-- --end() = [{0} {1}]",   
        it->first, it->second);   
    ++it;   
    System::Console::WriteLine("*--end() = [{0} {1}]",   
        it->first, it->second);   
    return (0);   
    }  
  
```  
  
  **\[un 1\] \[b 2\] \[c 3\]**  
**\*\-\- \-\-end\(\) \= \[b 2\]**  
**\*\-\-end\(\) \= \[c 3\]**   
## Requisitos  
 cliext \<de**Encabezado:** \/asignado\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [multimap](../dotnet/multimap-stl-clr.md)   
 [multimap::begin](../dotnet/multimap-begin-stl-clr.md)