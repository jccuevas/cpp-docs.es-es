---
title: "multimap::value_comp (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::multimap::value_comp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "value_comp (miembro) [STL/CLR]"
ms.assetid: 4d142014-ab39-4da3-8aa9-ad0ab0cfddf7
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# multimap::value_comp (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Copia el delegado de ordenación por dos valores de elemento.  
  
## Sintaxis  
  
```  
value_compare^ value_comp();  
```  
  
## Comentarios  
 La función miembro devuelve el delegado de ordenación utilizado para ordenar la secuencia controlada.  Se utiliza para comparar dos valores de elemento.  
  
## Ejemplo  
  
```  
// cliext_multimap_value_comp.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymultimap;   
int main()   
    {   
    Mymultimap c1;   
    Mymultimap::value_compare^ kcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare([L'a', 1], [L'a', 1]) = {0}",   
        kcomp(Mymultimap::make_value(L'a', 1),   
            Mymultimap::make_value(L'a', 1)));   
    System::Console::WriteLine("compare([L'a', 1], [L'b', 2]) = {0}",   
        kcomp(Mymultimap::make_value(L'a', 1),   
            Mymultimap::make_value(L'b', 2)));   
    System::Console::WriteLine("compare([L'b', 2], [L'a', 1]) = {0}",   
        kcomp(Mymultimap::make_value(L'b', 2),   
            Mymultimap::make_value(L'a', 1)));   
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
 [multimap](../dotnet/multimap-stl-clr.md)   
 [multimap::value\_compare](../dotnet/multimap-value-compare-stl-clr.md)   
 [multimap::value\_type](../dotnet/multimap-value-type-stl-clr.md)