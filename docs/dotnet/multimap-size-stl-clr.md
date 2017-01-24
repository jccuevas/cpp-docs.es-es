---
title: "multimap::size (STL/CLR) | Microsoft Docs"
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
  - "cliext::multimap::size"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "size (miembro) [STL/CLR]"
ms.assetid: 79a14142-a528-49ab-b4fd-340f5a4e70f9
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# multimap::size (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuenta el número de elementos.  
  
## Sintaxis  
  
```  
size_type size();  
```  
  
## Comentarios  
 La función miembro devuelve la longitud de la secuencia controlada.  Se utiliza para determinar el número de elementos actualmente en la secuencia controlada.  Si todo lo que se utiliza es de si la secuencia tiene un tamaño distinto de cero, vea [multimap::empty](../dotnet/multimap-empty-stl-clr.md)`()`.  
  
## Ejemplo  
  
```  
// cliext_multimap_size.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::multimap<wchar_t, int> Mymultimap;   
int main()   
    {   
    Mymultimap c1;   
    c1.insert(Mymultimap::make_value(L'a', 1));   
    c1.insert(Mymultimap::make_value(L'b', 2));   
    c1.insert(Mymultimap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymultimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0} after clearing", c1.size());   
  
// add elements and clear again   
    c1.insert(Mymultimap::make_value(L'd', 4));   
    c1.insert(Mymultimap::make_value(L'e', 5));   
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());   
    return (0);   
    }  
  
```  
  
  **\[un 1\] \[b 2\] \[c 3\]**  
**size\(\) \= 0 después de borrar**  
**size\(\) \= 2 después de agregar 2**   
## Requisitos  
 cliext \<de**Encabezado:** \/asignado\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [multimap](../dotnet/multimap-stl-clr.md)   
 [multimap::empty](../dotnet/multimap-empty-stl-clr.md)