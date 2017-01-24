---
title: "hash_map::rehash (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_map::rehash"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rehash (miembro) [STL/CLR]"
ms.assetid: e894157c-4e31-4fbf-8020-b90f236da3e7
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_map::rehash (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Recompila la tabla hash.  
  
## Sintaxis  
  
```  
void rehash();  
```  
  
## Comentarios  
 La función miembro recompila la tabla hash, lo que [hash\_map::load\_factor](../dotnet/hash-map-load-factor-stl-clr.md)`() <=` [hash\_map::max\_load\_factor](../dotnet/hash-map-max-load-factor-stl-clr.md).  Si no, la tabla hash aumente de tamaño sólo cuando sea necesario después de una inserción. \(Nunca automáticamente disminuye de tamaño\). Se utiliza para ajustar el tamaño de la tabla hash.  
  
## Ejemplo  
  
```  
// cliext_hash_map_rehash.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1 = gcnew Myhash_map;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// inspect current parameters   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    System::Console::WriteLine();   
  
// change max_load_factor and redisplay   
    c1.max_load_factor(0.25f);   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    System::Console::WriteLine();   
  
// rehash and redisplay   
    c1.rehash(100);   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    return (0);   
    }  
  
```  
  
  **\[un 1\] \[b 2\] \[c 3\]**  
**bucket\_count\(\) \= 16**  
**load\_factor\(\) \= 0,1875**  
**max\_load\_factor\(\) \= 4**  
**bucket\_count\(\) \= 16**  
**load\_factor\(\) \= 0,1875**  
**max\_load\_factor\(\) \= 0,25**  
**bucket\_count\(\) \= 128**  
**load\_factor\(\) \= 0,0234375**  
**max\_load\_factor\(\) \= 0,25**   
## Requisitos  
 cliext \<\/hash\_map de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [hash\_map](../dotnet/hash-map-stl-clr.md)   
 [hash\_map::bucket\_count](../dotnet/hash-map-bucket-count-stl-clr.md)   
 [hash\_map::load\_factor](../dotnet/hash-map-load-factor-stl-clr.md)   
 [hash\_map::max\_load\_factor](../dotnet/hash-map-max-load-factor-stl-clr.md)