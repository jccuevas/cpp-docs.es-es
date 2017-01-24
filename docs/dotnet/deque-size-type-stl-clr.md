---
title: "deque::size_type (STL/CLR) | Microsoft Docs"
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
  - "cliext::deque::size_type"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "size_type (miembro) [STL/CLR]"
ms.assetid: c598871c-0ce8-4599-ab4c-2d0ea5f3f8e4
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# deque::size_type (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El tipo de una distancia firmados entre el elemento dos.  
  
## Sintaxis  
  
```  
typedef int size_type;  
```  
  
## Comentarios  
 El tipo describe un recuento negativo del elemento.  
  
## Ejemplo  
  
```  
// cliext_deque_size_type.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    cliext::deque<wchar_t>::size_type diff = c1.end() - c1.begin();   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
    return (0);   
    }  
  
```  
  
  **a b c**  
**end\(\)\- inicio \(\) \= 3**   
## Requisitos  
 **Encabezado:** \<cliext\/deque\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [deque](../dotnet/deque-stl-clr.md)   
 [deque::empty](../dotnet/deque-empty-stl-clr.md)