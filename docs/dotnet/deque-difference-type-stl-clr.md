---
title: "deque::difference_type (STL/CLR) | Microsoft Docs"
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
  - "cliext::deque::difference_type"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "difference_type (miembro) [STL/CLR]"
ms.assetid: deb00a44-80c7-42f8-ad17-1d36377dec88
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# deque::difference_type (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los tipos de una distancia firmados entre dos elementos.  
  
## Sintaxis  
  
```  
typedef int difference_type;  
```  
  
## Comentarios  
 El tipo describe un recuento firmado del elemento.  
  
## Ejemplo  
  
```  
// cliext_deque_difference_type.cpp   
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
    cliext::deque<wchar_t>::difference_type diff = 0;   
    for (cliext::deque<wchar_t>::iterator it = c1.begin();   
        it != c1.end(); ++it) ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
  
// compute negative difference   
    diff = 0;   
    for (cliext::deque<wchar_t>::iterator it = c1.end();   
        it != c1.begin(); --it) --diff;   
    System::Console::WriteLine("begin()-end() = {0}", diff);   
    return (0);   
    }  
  
```  
  
  **a b c**  
**end\(\)\- inicio \(\) \= 3**  
**begin\(\)\- final \(\) \= \-3**   
## Requisitos  
 **Encabezado:** \<cliext\/deque\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [deque](../dotnet/deque-stl-clr.md)   
 [deque::size\_type](../dotnet/deque-size-type-stl-clr.md)