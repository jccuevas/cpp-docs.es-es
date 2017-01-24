---
title: "hash_multiset::operator= (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_multiset::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator= (miembro) [STL/CLR]"
ms.assetid: 1b4d5b0a-f10f-42f8-b67b-76af51c66baf
caps.latest.revision: 8
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_multiset::operator= (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Reemplaza la secuencia controlada.  
  
## Sintaxis  
  
```  
hash_multiset<Key>% operator=(hash_multiset<Key>% right);  
```  
  
#### Parámetros  
 right  
 Contenedor para copiar.  
  
## Comentarios  
 El miembro que el operador copia `right` al objeto, en que devuelve `*this`.  Se utiliza para reemplazar la secuencia controlada con una copia de la secuencia controlada en `right`.  
  
## Ejemplo  
  
```  
// cliext_hash_multiset_operator_as.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (Myhash_multiset::value_type elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myhash_multiset c2;   
    c2 = c1;   
// display contents " a b c"   
    for each (Myhash_multiset::value_type elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **a b c**   
## Requisitos  
 cliext \<\/hash\_set de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)