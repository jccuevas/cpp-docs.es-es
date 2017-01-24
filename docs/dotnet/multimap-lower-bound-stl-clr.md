---
title: "multimap::lower_bound (STL/CLR) | Microsoft Docs"
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
  - "cliext::multimap::lower_bound"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "lower_bound (miembro) [STL/CLR]"
ms.assetid: b8f9b2c2-ebcd-4553-b410-75fd8d472a49
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# multimap::lower_bound (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Encuentra el inicio del intervalo que coincide con una clave especificada.  
  
## Sintaxis  
  
```  
iterator lower_bound(key_type key);  
```  
  
#### Parámetros  
 clave  
 Valor de clave que se va a buscar.  
  
## Comentarios  
 La función miembro determina el primer elemento `X` en la secuencia controlada que tiene equivalente de ordenación a `key`.  Si no existe ningún elemento, devuelve [multimap::end](../dotnet/multimap-end-stl-clr.md)`()`; si no devuelve un iterador que señala `X`.  Se utiliza para buscar el principio de una secuencia de elementos actualmente en la secuencia controlada que coinciden con una clave especificada.  
  
## Ejemplo  
  
```  
// cliext_multimap_lower_bound.cpp   
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
  
    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",   
        c1.lower_bound(L'x') == c1.end());   
  
    Mymultimap::iterator it = c1.lower_bound(L'a');   
    System::Console::WriteLine("*lower_bound(L'a') = [{0} {1}]",   
        it->first, it->second);   
    it = c1.lower_bound(L'b');   
    System::Console::WriteLine("*lower_bound(L'b') = [{0} {1}]",   
        it->first, it->second);   
    return (0);   
    }  
  
```  
  
  **\[un 1\] \[b 2\] \[c 3\]**  
**lower\_bound\(L'x'\)\=\=end\(\) \= True**  
**\*lower\_bound \(L'a\) \= \[un 1\]**  
**\*lower\_bound \(L'b\) \= \[b 2\]**   
## Requisitos  
 cliext \<de**Encabezado:** \/asignado\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [multimap](../dotnet/multimap-stl-clr.md)   
 [multimap::count](../dotnet/multimap-count-stl-clr.md)   
 [multimap::equal\_range](../dotnet/multimap-equal-range-stl-clr.md)   
 [multimap::find](../dotnet/multimap-find-stl-clr.md)   
 [multimap::upper\_bound](../dotnet/multimap-upper-bound-stl-clr.md)