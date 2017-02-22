---
title: "set::reverse_iterator (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::set::reverse_iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "reverse_iterator (miembro) [STL/CLR]"
ms.assetid: 40337a62-991c-424e-9559-a9040c07657a
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# set::reverse_iterator (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El tipo de un iterador inverso para la secuencia controlada.  
  
## Sintaxis  
  
```  
typedef T3 reverse_iterator;  
```  
  
## Comentarios  
 El tipo describe un objeto de tipo sin especificar `T3` que sirva como iterador inverso para la secuencia controlada.  
  
## Ejemplo  
  
```  
// cliext_set_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" reversed   
    Myset::reverse_iterator rit = c1.rbegin();   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" {0}", *rit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **b a c**   
## Requisitos  
 cliext \<o conjunto de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [set](../dotnet/set-stl-clr.md)   
 [set::const\_iterator](../dotnet/set-const-iterator-stl-clr.md)   
 [set::const\_reverse\_iterator](../dotnet/set-const-reverse-iterator-stl-clr.md)   
 [set::iterator](../dotnet/set-iterator-stl-clr.md)