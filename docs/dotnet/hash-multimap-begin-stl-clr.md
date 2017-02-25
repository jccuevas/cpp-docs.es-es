---
title: "hash_multimap::begin (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::hash_multimap::begin"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "begin (miembro) [STL/CLR]"
ms.assetid: 7f8d51c1-8183-4dc1-9dfc-f58dbf594c42
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# hash_multimap::begin (STL/CLR)
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
// cliext_hash_multimap_begin.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_multimap<wchar_t, int> Myhash_multimap;   
int main()   
    {   
    Myhash_multimap c1;   
    c1.insert(Myhash_multimap::make_value(L'a', 1));   
    c1.insert(Myhash_multimap::make_value(L'b', 2));   
    c1.insert(Myhash_multimap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_multimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// inspect first two items   
    Myhash_multimap::iterator it = c1.begin();   
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
 cliext \<\/hash\_map de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [hash\_multimap](../dotnet/hash-multimap-stl-clr.md)   
 [hash\_multimap::end](../dotnet/hash-multimap-end-stl-clr.md)