---
title: "operator&lt; (list) (STL/CLR) | Microsoft Docs"
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
  - "cliext::list::operator<"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator< (miembro) [STL/CLR]"
ms.assetid: 6990fac2-3eeb-481f-b289-1c93f51422e4
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# operator&lt; (list) (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Lista menos que comparación.  
  
## Sintaxis  
  
```  
template<typename Value>  
    bool operator<(list<Value>% left,  
        list<Value>% right);  
```  
  
#### Parámetros  
 left  
 Contenedor izquierdo a comparar.  
  
 right  
 Contenedor derecho a comparar.  
  
## Comentarios  
 La función de operador devuelve true si, para la posición inferior `i` para la que `!(``right``[i] <` `left``[i])` también son true que `left``[i] <` `right``[i]`.  De lo contrario, devuelve el uso de `left``->size() <` `right``->size()` Que consiste en probar si `left` se le antes de `right` cuando las dos listas son elemento comparado al lado de elemento.  
  
## Ejemplo  
  
```  
// cliext_list_operator_lt.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::list<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
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
 cliext \<de**Encabezado:** \/enumerado\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [list](../dotnet/list-stl-clr.md)   
 [operator\=\= \(list\)](../dotnet/operator-equality-list-stl-clr.md)   
 [operator\!\= \(list\)](../dotnet/operator-inequality-list-stl-clr.md)   
 [operator\>\= \(list\)](../dotnet/operator-greater-or-equal-list-stl-clr.md)   
 [operator\> \(list\)](../dotnet/operator-greater-than-list-stl-clr.md)   
 [operator\<\= \(list\)](../dotnet/operator-less-or-equal-list-stl-clr.md)