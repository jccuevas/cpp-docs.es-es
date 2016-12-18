---
title: "operator&lt; (queue) (STL/CLR) | Microsoft Docs"
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
  - "cliext::queue::operator<"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator< (miembro) [STL/CLR]"
ms.assetid: 2c981e2b-9a88-4b4a-8060-9ac24d5631f5
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# operator&lt; (queue) (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cola menos que comparación.  
  
## Sintaxis  
  
```  
template<typename Value,  
    typename Container>  
    bool operator<(queue<Value, Container>% left,  
        queue<Value, Container>% right);  
```  
  
#### Parámetros  
 left  
 Contenedor izquierdo a comparar.  
  
 right  
 Contenedor derecho a comparar.  
  
## Comentarios  
 La función de operador devuelve true si, para la posición inferior `i` para la que `!(``right``[i] <` `left``[i])` también son true que `left``[i] <` `right``[i]`.  De lo contrario, devuelve el uso de `left``->`[queue::size](../dotnet/queue-size-stl-clr.md)`() <` `right``->size()` Que consiste en probar si `left` se le antes de `right` cuando las dos colas son elemento comparado al lado de elemento.  
  
## Ejemplo  
  
```  
// cliext_queue_operator_lt.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myqueue c2;   
    c2.push(L'a');   
    c2.push(L'b');   
    c2.push(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] < [a b c] is {0}",   
        c1 < c1);   
    System::Console::WriteLine("[a b c] < [a b d] is {0}",   
        c1 < c2);   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **una d b**  
**\[una c\] \< b \[una b c\] es False**  
**\[una c\] \< b \[una d b\] es True**   
## Requisitos  
 cliext \<\/cola de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [queue](../dotnet/queue-stl-clr.md)   
 [operator\=\= \(queue\)](../dotnet/operator-equality-queue-stl-clr.md)   
 [operator\!\= \(queue\)](../dotnet/operator-inequality-queue-stl-clr.md)   
 [operator\>\= \(queue\)](../dotnet/operator-greater-or-equal-queue-stl-clr.md)   
 [operator\> \(queue\)](../dotnet/operator-greater-than-queue-stl-clr.md)   
 [operator\<\= \(queue\)](../dotnet/operator-less-or-equal-queue-stl-clr.md)