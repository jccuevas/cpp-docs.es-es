---
title: "hash_set::key_type (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::hash_set::key_type"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "key_type (miembro) [STL/CLR]"
ms.assetid: e79180b5-4fea-4884-93a7-1738d15c6126
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# hash_set::key_type (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El tipo de una clave de ordenación.  
  
## Sintaxis  
  
```  
typedef Key key_type;  
```  
  
## Comentarios  
 El tipo es un sinónimo para el parámetro `Key`de la plantilla.  
  
## Ejemplo  
  
```  
// cliext_hash_set_key_type.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" using key_type   
    for (Myhash_set::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in key_type object   
        Myhash_set::key_type val = *it;   
  
        System::Console::Write(" {0}", val);   
        }   
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
 [hash\_set::key\_compare](../dotnet/hash-set-key-compare-stl-clr.md)   
 [hash\_set::value\_type](../dotnet/hash-set-value-type-stl-clr.md)