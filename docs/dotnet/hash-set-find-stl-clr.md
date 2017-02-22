---
title: "hash_set::find (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::hash_set::find"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "find (miembro) [STL/CLR]"
ms.assetid: 758b7438-ef15-4af0-8001-a1126d5e9a9e
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# hash_set::find (STL/CLR)
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
 Si por lo menos un elemento de la secuencia controlada tiene equivalente de ordenación con `key`, la función miembro devuelve un iterador que elija uno de esos elementos; si no devuelve [hash\_set::end](../dotnet/hash-set-end-stl-clr.md)`()`.  Se utiliza para buscar un elemento actualmente en la secuencia controlada que coincide con una clave especificada.  
  
## Ejemplo  
  
```  
// cliext_hash_set_find.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("find {0} = {1}",   
        L'A', c1.find(L'A') != c1.end());   
    System::Console::WriteLine("find {0} = {1}",   
        L'b', *c1.find(L'b'));   
    System::Console::WriteLine("find {0} = {1}",   
        L'C', c1.find(L'C') != c1.end());   
    return (0);   
    }  
  
```  
  
  **a b c**  
**busque A \= False**  
**busque la b \= b**  
**busque C \= False**   
## Descripción  
 Observe que `find` no garantiza cuáles de varios encuentra el elemento él.  
  
## Requisitos  
 cliext \<\/hash\_set de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [hash\_set](../dotnet/hash-set-stl-clr.md)   
 [hash\_set::equal\_range](../dotnet/hash-set-equal-range-stl-clr.md)   
 [hash\_set::lower\_bound](../dotnet/hash-set-lower-bound-stl-clr.md)   
 [hash\_set::upper\_bound](../dotnet/hash-set-upper-bound-stl-clr.md)