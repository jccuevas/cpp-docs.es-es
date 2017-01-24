---
title: "priority_queue::value_comp (STL/CLR) | Microsoft Docs"
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
  - "cliext::priority_queue::value_comp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "value_comp (miembro) [STL/CLR]"
ms.assetid: af28e541-087d-4837-9ff0-cd36d4cfc57a
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# priority_queue::value_comp (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Copia el delegado de ordenación de dos elementos.  
  
## Sintaxis  
  
```  
value_compare^ value_comp();  
```  
  
## Comentarios  
 La función miembro devuelve el delegado de ordenación utilizado para ordenar la secuencia controlada.  Se usa para comparar dos valores.  
  
## Ejemplo  
  
```  
// cliext_priority_queue_value_comp.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    Mypriority_queue::value_compare^ vcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        vcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        vcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        vcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Mypriority_queue c2 = cliext::greater<wchar_t>();   
    vcomp = c2.value_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        vcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        vcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        vcomp(L'b', L'a'));   
    return (0);   
    }  
  
```  
  
  **comparar \(L'a, L'a\) \= False**  
**comparar \(L'a, L'b\) \= True**  
**comparar \(L'b, L'a\) \= False**  
**comparar \(L'a, L'a\) \= False**  
**comparar \(L'a, L'b\) \= False**  
**comparar \(L'b, L'a\) \= True**   
## Requisitos  
 cliext \<\/cola de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [priority\_queue](../dotnet/priority-queue-stl-clr.md)   
 [priority\_queue::value\_compare](../dotnet/priority-queue-value-compare-stl-clr.md)   
 [priority\_queue::value\_type](../dotnet/priority-queue-value-type-stl-clr.md)