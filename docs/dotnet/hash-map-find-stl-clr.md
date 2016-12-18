---
title: "hash_map::find (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_map::find"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "find (miembro) [STL/CLR]"
ms.assetid: 53ff8d57-2ea4-485e-9419-aed5e3f5affb
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_map::find (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Busca un elemento que coincida con una clave especificada.  
  
## Sintaxis  
  
```  
iterator find(key_type key);  
```  
  
#### Parámetros  
 clave  
 Valor de clave que se va a buscar.  
  
## Comentarios  
 Si por lo menos un elemento de la secuencia controlada tiene equivalente de ordenación con `key`, la función miembro devuelve un iterador que elija uno de esos elementos; si no devuelve [hash\_map::end](../dotnet/hash-map-end-stl-clr.md)`()`.  Se utiliza para buscar un elemento actualmente en la secuencia controlada que coincide con una clave especificada.  
  
## Ejemplo  
  
```  
// cliext_hash_map_find.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("find {0} = {1}",   
        L'A', c1.find(L'A') != c1.end());   
  
    Myhash_map::iterator it = c1.find(L'b');   
    System::Console::WriteLine("find {0} = [{1} {2}]",   
        L'b', it->first, it->second);   
  
    System::Console::WriteLine("find {0} = {1}",   
        L'C', c1.find(L'C') != c1.end());   
    return (0);   
    }  
  
```  
  
  **\[un 1\] \[b 2\] \[c 3\]**  
**busque A \= False**  
**b de búsqueda \= \[b 2\]**  
**busque C \= False**   
## Descripción  
 Observe que `find` no garantiza cuáles de varios encuentra el elemento él.  
  
## Requisitos  
 cliext \<\/hash\_map de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [hash\_map](../dotnet/hash-map-stl-clr.md)   
 [hash\_map::equal\_range](../dotnet/hash-map-equal-range-stl-clr.md)   
 [hash\_map::lower\_bound](../dotnet/hash-map-lower-bound-stl-clr.md)   
 [hash\_map::upper\_bound](../dotnet/hash-map-upper-bound-stl-clr.md)