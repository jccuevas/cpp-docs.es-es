---
title: "map::value_compare (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::map::value_compare"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "value_compare (miembro) [STL/CLR]"
ms.assetid: 04fab34b-c68a-4f61-97e8-a7d629b1ffed
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# map::value_compare (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El delegado de ordenación por dos valores de elemento.  
  
## Sintaxis  
  
```  
Microsoft::VisualC::StlClr::BinaryDelegate<generic_value, generic_value, bool>  
    value_compare;  
```  
  
## Comentarios  
 El tipo es un sinónimo del delegado que determina el orden de sus argumentos de valor.  
  
## Ejemplo  
  
```  
// cliext_map_value_compare.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    Mymap::value_compare^ kcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare([L'a', 1], [L'a', 1]) = {0}",   
        kcomp(Mymap::make_value(L'a', 1),   
            Mymap::make_value(L'a', 1)));   
    System::Console::WriteLine("compare([L'a', 1], [L'b', 2]) = {0}",   
        kcomp(Mymap::make_value(L'a', 1),   
            Mymap::make_value(L'b', 2)));   
    System::Console::WriteLine("compare([L'b', 2], [L'a', 1]) = {0}",   
        kcomp(Mymap::make_value(L'b', 2),   
            Mymap::make_value(L'a', 1)));   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **comparar \(\[L'a, 1\], \[L'a, 1\]\) \= False**  
**comparar \(\[L'a, 1\], \[L'b, 2\]\) \= True**  
**comparar \(\[L'b, 2\], \[L'a, 1\]\) \= False**   
## Requisitos  
 cliext \<de**Encabezado:** \/asignado\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [map](../dotnet/map-stl-clr.md)   
 [map::key\_compare](../dotnet/map-key-compare-stl-clr.md)   
 [map::value\_comp](../dotnet/map-value-comp-stl-clr.md)   
 [map::value\_type](../dotnet/map-value-type-stl-clr.md)