---
title: "multimap::equal_range (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::multimap::equal_range"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "equal_range (miembro) [STL/CLR]"
ms.assetid: f1008d89-7442-429b-9eca-4ef7ee704766
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# multimap::equal_range (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Encuentra el intervalo que coincide con una clave especificada.  
  
## Sintaxis  
  
```  
pair_iter_iter equal_range(key_type _Keyval);  
```  
  
#### Parámetros  
 `_Keyval`  
 Valor de clave que se va a buscar.  
  
## Comentarios  
 El método devuelve un par de iteradores `-` [multimap::lower\_bound](../dotnet/multimap-lower-bound-stl-clr.md)`(``_Keyval``),` [multimap::upper\_bound](../dotnet/multimap-upper-bound-stl-clr.md)`(``_Keyval``)`.  Se utiliza para determinar el intervalo de elementos actualmente en la secuencia controlada que coinciden con una clave especificada.  
  
## Ejemplo  
  
```  
// cliext_multimap_equal_range.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::multimap<wchar_t, int> Mymultimap;   
typedef Mymultimap::pair_iter_iter Pairii;   
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
  
// display results of failed search   
    Pairii pair1 = c1.equal_range(L'x');   
    System::Console::WriteLine("equal_range(L'x') empty = {0}",   
        pair1.first == pair1.second);   
  
// display results of successful search   
    pair1 = c1.equal_range(L'b');   
    for (; pair1.first != pair1.second; ++pair1.first)   
        System::Console::Write(" [{0} {1}]",   
            pair1.first->first, pair1.first->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **\[un 1\] \[b 2\] \[c 3\]**  
**el equal\_range \(L'x\) vacía \= True**  
 **\[b 2\]**   
## Requisitos  
 cliext \<de**Encabezado:** \/asignado\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [multimap](../dotnet/multimap-stl-clr.md)   
 [multimap::count](../dotnet/multimap-count-stl-clr.md)   
 [multimap::find](../dotnet/multimap-find-stl-clr.md)   
 [multimap::lower\_bound](../dotnet/multimap-lower-bound-stl-clr.md)   
 [multimap::upper\_bound](../dotnet/multimap-upper-bound-stl-clr.md)