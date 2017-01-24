---
title: "map::make_value (STL/CLR) | Microsoft Docs"
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
  - "cliext::map::make_value"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "make_value (miembro) [STL/CLR]"
ms.assetid: a0bc4081-b8b7-450e-b041-a49ac42b279f
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# map::make_value (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Construye un objeto value.  
  
## Sintaxis  
  
```  
static value_type make_value(key_type key, mapped_type mapped);  
```  
  
#### Parámetros  
 clave  
 Valor de clave a utilizar.  
  
 asignado  
 Valor asignado a buscar.  
  
## Comentarios  
 La función miembro devuelve un objeto de `value_type` cuya clave se `key` y cuyo asignaban valor son `mapped`.  Se utiliza para crear un objeto adecuado para el uso con otras funciones miembro.  
  
## Ejemplo  
  
```  
// cliext_map_make_value.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **\[un 1\] \[b 2\] \[c 3\]**   
## Requisitos  
 cliext \<de**Encabezado:** \/asignado\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [map](../dotnet/map-stl-clr.md)   
 [map::key\_type](../dotnet/map-key-type-stl-clr.md)   
 [map::mapped\_type](../dotnet/map-mapped-type-stl-clr.md)   
 [map::value\_type](../dotnet/map-value-type-stl-clr.md)