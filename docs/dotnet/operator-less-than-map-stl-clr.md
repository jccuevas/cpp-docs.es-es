---
title: "operator&lt; (map) (STL/CLR) | Microsoft Docs"
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
  - "cliext::map::operator<"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator< (miembro) [STL/CLR]"
ms.assetid: 9ff87b44-663e-4b99-9dba-d775d9f6f853
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# operator&lt; (map) (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Lista menos que comparación.  
  
## Sintaxis  
  
```  
template<typename Key,  
    typename Mapped>  
    bool operator<(map<Key, Mapped>% left,  
        map<Key, Mapped>% right);  
```  
  
#### Parámetros  
 left  
 Contenedor izquierdo a comparar.  
  
 right  
 Contenedor derecho a comparar.  
  
## Comentarios  
 La función de operador devuelve true si, para la posición inferior `i` para la que `!(``right``[i] <` `left``[i])` también son true que `left``[i] <` `right``[i]`.  De lo contrario, devuelve el uso de `left``->size() <` `right``->size()` Que consiste en probar si `left` se le antes de `right` cuando los dos asignaciones son elemento comparado al lado de elemento.  
  
## Ejemplo  
  
```  
// cliext_map_operator_lt.cpp   
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
  
// assign to a new container   
    Mymap c2;   
    c2.insert(Mymap::make_value(L'a', 1));   
    c2.insert(Mymap::make_value(L'b', 2));   
    c2.insert(Mymap::make_value(L'd', 4));   
  
// display contents " [a 1] [b 2] [d 4]"   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] < [a b c] is {0}",   
        c1 < c1);   
    System::Console::WriteLine("[a b c] < [a b d] is {0}",   
        c1 < c2);   
    return (0);   
    }  
  
```  
  
  **\[un 1\] \[b 2\] \[c 3\]**  
 **\[un 1\] \[b 2\] \[d 4\]**  
**\[una c\] \< b \[una b c\] es False**  
**\[una c\] \< b \[una d b\] es True**   
## Requisitos  
 cliext \<de**Encabezado:** \/asignado\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [map](../dotnet/map-stl-clr.md)   
 [operator\=\= \(map\)](../dotnet/operator-equality-map-stl-clr.md)   
 [operator\!\= \(map\)](../dotnet/operator-inequality-map-stl-clr.md)   
 [operator\>\= \(map\)](../dotnet/operator-greater-or-equal-map-stl-clr.md)   
 [operator\> \(map\)](../dotnet/operator-greater-than-map-stl-clr.md)   
 [operator\<\= \(map\)](../dotnet/operator-less-or-equal-map-stl-clr.md)