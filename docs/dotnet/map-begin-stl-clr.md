---
title: "map::begin (STL/CLR) | Microsoft Docs"
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
  - "cliext::map::begin"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "begin (miembro) [STL/CLR]"
ms.assetid: a909d278-6214-4e11-984d-509fa528bfa3
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# map::begin (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Designa el principio de la secuencia controlada.  
  
## Sintaxis  
  
```  
iterator begin();  
```  
  
## Comentarios  
 La función miembro devuelve un iterador bidireccional que señala el primer elemento de la secuencia controlada, o simplemente más allá del final de una secuencia vacía.  Se usa para obtener un iterador que designe el principio de la secuencia controlada, indicado por `current`, pero su estado puede cambiar si cambia la longitud de la secuencia controlada.  
  
## Ejemplo  
  
```  
// cliext_map_begin.cpp   
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
  
// inspect first two items   
    Mymap::iterator it = c1.begin();   
    System::Console::WriteLine("*begin() = [{0} {1}]",   
        it->first, it->second);   
    ++it;   
    System::Console::WriteLine("*++begin() = [{0} {1}]",   
        it->first, it->second);   
    return (0);   
    }  
  
```  
  
  **\[un 1\] \[b 2\] \[c 3\]**  
**\*begin\(\) \= \[un 1\]**  
**\*\+\+begin\(\) \= \[b 2\]**   
## Requisitos  
 cliext \<de**Encabezado:** \/asignado\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [map](../dotnet/map-stl-clr.md)   
 [map::end](../dotnet/map-end-stl-clr.md)