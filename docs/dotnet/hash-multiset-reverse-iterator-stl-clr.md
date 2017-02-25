---
title: "hash_multiset::reverse_iterator (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::hash_multiset::reverse_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "reverse_iterator (miembro) [STL/CLR]"
ms.assetid: a988adca-8fd7-4678-9edc-041555a3561d
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# hash_multiset::reverse_iterator (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El tipo de un iterador inverso para la secuencia controlada.  
  
## Sintaxis  
  
```  
typedef T3 reverse_iterator;  
```  
  
## Comentarios  
 El tipo describe un objeto de tipo sin especificar `T3` que sirva como iterador inverso para la secuencia controlada.  
  
## Ejemplo  
  
```  
// cliext_hash_multiset_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" reversed   
    Myhash_multiset::reverse_iterator rit = c1.rbegin();   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" {0}", *rit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **b a c**   
## Requisitos  
 cliext \<\/hash\_set de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_multiset::const\_iterator](../dotnet/hash-multiset-const-iterator-stl-clr.md)   
 [hash\_multiset::const\_reverse\_iterator](../dotnet/hash-multiset-const-reverse-iterator-stl-clr.md)   
 [hash\_multiset::iterator](../dotnet/hash-multiset-iterator-stl-clr.md)