---
title: "hash_map::lower_bound (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::hash_map::lower_bound"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "lower_bound (miembro) [STL/CLR]"
ms.assetid: 7c88987a-9c77-4874-8052-192a148abbf1
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# hash_map::lower_bound (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Encuentra el inicio del intervalo que coincide con una clave especificada.  
  
## Sintaxis  
  
```  
iterator lower_bound(key_type key);  
```  
  
#### Parámetros  
 clave  
 Valor de clave que se va a buscar.  
  
## Comentarios  
 La función miembro determina el primer elemento `X` en la secuencia controlada que aplica un algoritmo hash al mismo depósito que `key` y tiene equivalente de ordenación a `key`.  Si no existe ningún elemento, devuelve [hash\_map::end](../dotnet/hash-map-end-stl-clr.md)`()`; si no devuelve un iterador que señala `X`.  Se utiliza para buscar el principio de una secuencia de elementos actualmente en la secuencia controlada que coinciden con una clave especificada.  
  
## Ejemplo  
  
```  
// cliext_hash_map_lower_bound.cpp   
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
  
    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",   
        c1.lower_bound(L'x') == c1.end());   
  
    Myhash_map::iterator it = c1.lower_bound(L'a');   
    System::Console::WriteLine("*lower_bound(L'a') = [{0} {1}]",   
        it->first, it->second);   
    it = c1.lower_bound(L'b');   
    System::Console::WriteLine("*lower_bound(L'b') = [{0} {1}]",   
        it->first, it->second);   
    return (0);   
    }  
  
```  
  
  **\[un 1\] \[b 2\] \[c 3\]**  
**lower\_bound\(L'x'\)\=\=end\(\) \= True**  
**\*lower\_bound \(L'a\) \= \[un 1\]**  
**\*lower\_bound \(L'b\) \= \[b 2\]**   
## Requisitos  
 cliext \<\/hash\_map de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [hash\_map](../dotnet/hash-map-stl-clr.md)   
 [hash\_map::count](../dotnet/hash-map-count-stl-clr.md)   
 [hash\_map::equal\_range](../dotnet/hash-map-equal-range-stl-clr.md)   
 [hash\_map::find](../dotnet/hash-map-find-stl-clr.md)   
 [hash\_map::upper\_bound](../dotnet/hash-map-upper-bound-stl-clr.md)