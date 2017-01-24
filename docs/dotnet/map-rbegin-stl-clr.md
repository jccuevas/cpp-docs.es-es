---
title: "map::rbegin (STL/CLR) | Microsoft Docs"
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
  - "cliext::map::rbegin"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rbegin (miembro) [STL/CLR]"
ms.assetid: bd7165a3-561f-48d4-9791-7aaafc2cf3a5
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# map::rbegin (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Designa el principio de la secuencia controlada inversa.  
  
## Sintaxis  
  
```  
reverse_iterator rbegin();  
```  
  
## Comentarios  
 La función miembro devuelve un iterador inversa que señale el último elemento de la secuencia controlada, o simplemente más allá del principio de una secuencia vacía.  Por lo tanto, designa el parámetro `beginning` de la secuencia inversa.  Se usa para obtener un iterador que designe el principio de la secuencia controlada mostrada en orden inverso, indicado por `current`, pero su estado puede cambiar si cambia la longitud de la secuencia controlada.  
  
## Ejemplo  
  
```  
// cliext_map_rbegin.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// inspect first two items in reversed sequence   
    Mymap::reverse_iterator rit = c1.rbegin();   
    System::Console::WriteLine("*rbegin() = [{0} {1}]",   
        rit->first, rit->second);   
    ++rit;   
    System::Console::WriteLine("*++rbegin() = [{0} {1}]",   
        rit->first, rit->second);   
    return (0);   
    }  
  
```  
  
  **\[un 1\] \[b 2\] \[c 3\]**  
**\*rbegin\(\) \= \[c 3\]**  
**\*\+\+rbegin\(\) \= \[b 2\]**   
## Requisitos  
 cliext \<de**Encabezado:** \/asignado\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [map](../dotnet/map-stl-clr.md)   
 [map::begin](../dotnet/map-begin-stl-clr.md)   
 [map::end](../dotnet/map-end-stl-clr.md)   
 [map::rend](../dotnet/map-rend-stl-clr.md)