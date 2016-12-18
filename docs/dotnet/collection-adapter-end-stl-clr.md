---
title: "collection_adapter::end (STL/CLR) | Microsoft Docs"
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
  - "cliext::collection_adapter::end"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "end (miembro) [STL/CLR]"
ms.assetid: f953a734-2f17-4b68-9ca4-34f980d08887
caps.latest.revision: 9
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# collection_adapter::end (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Designa el final de la secuencia controlada.  
  
## Sintaxis  
  
```  
iterator end();  
```  
  
## Comentarios  
 La función miembro devuelve un iterador de entrada que señala simplemente más allá del final de la secuencia controlada.  
  
## Ejemplo  
  
```  
// cliext_collection_adapter_end.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
    Mycoll c1(%d1);   
  
// display initial contents " a b c"   
    Mycoll::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**   
## Requisitos  
 cliext \<\/adaptador de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [collection\_adapter](../dotnet/collection-adapter-stl-clr.md)   
 [collection\_adapter::begin](../dotnet/collection-adapter-begin-stl-clr.md)