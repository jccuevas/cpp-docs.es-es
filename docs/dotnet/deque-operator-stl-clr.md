---
title: "deque::operator(STL/CLR) | Microsoft Docs"
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
  - "cliext::deque::operator[]"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator[] (miembro) [STL/CLR]"
ms.assetid: d7653bb5-db48-4637-a25c-e7303e5d28da
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# deque::operator(STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Tiene acceso a un elemento en una posición especificada.  
  
## Sintaxis  
  
```  
reference operator[](size_type pos);  
```  
  
#### Parámetros  
 posición  
 Posición del elemento al que se va a tener acceso.  
  
## Comentarios  
 El operador de miembro devuelve un referene al elemento en la posición `pos`.  Se utiliza para tener acceso a un elemento cuya posición sepa.  
  
## Ejemplo  
  
```  
// cliext_deque_operator_sub.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" using subscripting   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1[i]);   
    System::Console::WriteLine();   
  
// change an entry and redisplay   
    c1[1] = L'x';   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1[i]);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **una c de x**   
## Requisitos  
 **Encabezado:** \<cliext\/deque\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [deque](../dotnet/deque-stl-clr.md)   
 [deque::at](../dotnet/deque-at-stl-clr.md)