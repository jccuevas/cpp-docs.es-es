---
title: "vector::const_reverse_iterator (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::vector::const_reverse_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "const_reverse_iterator (miembro) [STL/CLR]"
ms.assetid: 5e0a8597-7da4-4545-8826-446a8ee6412d
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# vector::const_reverse_iterator (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El tipo de un iterador inverso constante para la secuencia controlada.  
  
## Sintaxis  
  
```  
typedef T4 const_reverse_iterator;  
```  
  
## Comentarios  
 El tipo describe un objeto de tipo sin especificar `T4` que sirva como iterador inverso constante para la secuencia controlada.  
  
## Ejemplo  
  
```  
// cliext_vector_const_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" reversed   
    cliext::vector<wchar_t>::const_reverse_iterator crit = c1.rbegin();   
    cliext::vector<wchar_t>::const_reverse_iterator crend = c1.rend();   
    for (; crit != crend; ++crit)   
        System::Console::Write(" {0}", *crit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **b a c**   
## Requisitos  
 cliext \<\/vector de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [vector](../dotnet/vector-stl-clr.md)   
 [vector::reverse\_iterator](../dotnet/vector-reverse-iterator-stl-clr.md)