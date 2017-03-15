---
title: "operator&gt; (queue) (STL/CLR) | Microsoft Docs"
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
  - "cliext::queue::operator>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator> (miembro) [STL/CLR]"
ms.assetid: 40396a01-b2b6-4921-a1eb-f8704b015b75
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# operator&gt; (queue) (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cola mayor que comparación.  
  
## Sintaxis  
  
```  
template<typename Value,  
    typename Container>  
    bool operator>(queue<Value, Container>% left,  
        queue<Value, Container>% right);  
```  
  
#### Parámetros  
 left  
 Contenedor izquierdo a comparar.  
  
 right  
 Contenedor derecho a comparar.  
  
## Comentarios  
 La función de operador devuelve `right` `<` `left`.  Se utiliza para probar si `left` se le después de `right` cuando las dos colas son elemento comparado al lado de elemento.  
  
## Ejemplo  
  
```  
// cliext_queue_operator_gt.cpp   
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
  
    System::Console::WriteLine("[a b c] > [a b c] is {0}",   
        c1 > c1);   
    System::Console::WriteLine("[a b d] > [a b c] is {0}",   
        c2 > c1);   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **una d b**  
**\[una c\] \> b \[una b c\] es False**  
**\[una d\] \> b \[una b c\] es True**   
## Requisitos  
 cliext \<\/cola de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [queue](../dotnet/queue-stl-clr.md)   
 [operator\=\= \(queue\)](../dotnet/operator-equality-queue-stl-clr.md)   
 [operator\!\= \(queue\)](../dotnet/operator-inequality-queue-stl-clr.md)   
 [operator\< \(queue\)](../dotnet/operator-less-than-queue-stl-clr.md)   
 [operator\>\= \(queue\)](../dotnet/operator-greater-or-equal-queue-stl-clr.md)   
 [operator\<\= \(queue\)](../dotnet/operator-less-or-equal-queue-stl-clr.md)