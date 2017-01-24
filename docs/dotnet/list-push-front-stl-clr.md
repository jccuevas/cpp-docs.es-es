---
title: "list::push_front (STL/CLR) | Microsoft Docs"
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
  - "cliext::list::push_front"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "push_front (miembro) [STL/CLR]"
ms.assetid: 47525641-1139-44fc-ac62-bdc04876d9e0
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# list::push_front (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Agrega un nuevo primero.  
  
## Sintaxis  
  
```  
void push_front(value_type val);  
```  
  
## Comentarios  
 La función miembro inserta un elemento con el valor `val` al principio de la secuencia controlada.  Se utiliza para anteponer otro elemento a la lista.  
  
## Ejemplo  
  
```  
// cliext_list_push_front.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_front(L'a');   
    c1.push_front(L'b');   
    c1.push_front(L'c');   
  
// display contents " c b a"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **b a c**   
## Requisitos  
 cliext \<de**Encabezado:** \/enumerado\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [list](../dotnet/list-stl-clr.md)   
 [list::pop\_back](../dotnet/list-pop-back-stl-clr.md)   
 [list::pop\_front](../dotnet/list-pop-front-stl-clr.md)   
 [list::push\_back](../dotnet/list-push-back-stl-clr.md)