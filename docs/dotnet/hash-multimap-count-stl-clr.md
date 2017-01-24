---
title: "hash_multimap::count (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_multimap::Count"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "count (miembro) [STL/CLR]"
ms.assetid: a4bc5b19-e025-4063-9797-304ab4ba08aa
caps.latest.revision: 18
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_multimap::count (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Busca el número de elementos que coinciden con una clave especificada.  
  
## Sintaxis  
  
```  
size_type count(key_type key);  
```  
  
#### Parámetros  
 clave  
 Valor de clave que se va a buscar.  
  
## Comentarios  
 La función miembro devuelve el número de elementos de la secuencia controlada que tienen equivalente de ordenación con `key`.  Se usa para determinar el número de elementos que están actualmente en la secuencia controlada que coinciden con una clave especificada.  
  
## Ejemplo  
  
```  
// cliext_hash_multimap_count.cpp   
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
  
    System::Console::WriteLine("count(L'A') = {0}", c1.count(L'A'));   
    System::Console::WriteLine("count(L'b') = {0}", c1.count(L'b'));   
    System::Console::WriteLine("count(L'C') = {0}", c1.count(L'C'));   
    return (0);   
    }  
  
```  
  
  **\[un 1\] \[b 2\] \[c 3\]**  
**count \(L'A\) \= 0**  
**count \(L'b\) \= 1**  
**count \(L'C\) \= 0**   
## Requisitos  
 cliext \<\/hash\_map de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [hash\_multimap](../dotnet/hash-multimap-stl-clr.md)   
 [hash\_multimap::equal\_range](../dotnet/hash-multimap-equal-range-stl-clr.md)