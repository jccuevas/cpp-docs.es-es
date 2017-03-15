---
title: "hash_set::const_iterator (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::hash_set::const_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "const_iterator (miembro) [STL/CLR]"
ms.assetid: 5b346a3e-cdbb-4300-9b25-a16a5f74f9b2
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# hash_set::const_iterator (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El tipo de un iterador constante para la secuencia controlada.  
  
## Sintaxis  
  
```  
typedef T2 const_iterator;  
```  
  
## Comentarios  
 El tipo describe un objeto de tipo sin especificar `T2` que sirva como iterador bidireccional constante para la secuencia controlada.  
  
## Ejemplo  
  
```  
// cliext_hash_set_const_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    Myhash_set::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        System::Console::Write(" {0}", *cit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**   
## Requisitos  
 cliext \<\/hash\_set de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [hash\_set](../dotnet/hash-set-stl-clr.md)   
 [hash\_set::iterator](../dotnet/hash-set-iterator-stl-clr.md)