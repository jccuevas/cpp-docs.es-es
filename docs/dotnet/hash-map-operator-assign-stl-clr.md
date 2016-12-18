---
title: "hash_map::operator= (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_map::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator= (miembro) [STL/CLR]"
ms.assetid: fbcbae4c-c8f8-431e-831b-a40cce00a88c
caps.latest.revision: 8
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_map::operator= (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Reemplaza la secuencia controlada.  
  
## Sintaxis  
  
```  
hash_map<Key, Mapped>% operator=(hash_map<Key, Mapped>% right);  
```  
  
#### Parámetros  
 right  
 Contenedor para copiar.  
  
## Comentarios  
 El miembro que el operador copia `right` al objeto, en que devuelve `*this`.  Se utiliza para reemplazar la secuencia controlada con una copia de la secuencia controlada en `right`.  
  
## Ejemplo  
  
```  
// cliext_hash_map_operator_as.cpp   
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
  
// assign to a new container   
    Myhash_map c2;   
    c2 = c1;   
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **\[un 1\] \[b 2\] \[c 3\]**  
 **\[un 1\] \[b 2\] \[c 3\]**   
## Requisitos  
 cliext \<\/hash\_map de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [hash\_map](../dotnet/hash-map-stl-clr.md)