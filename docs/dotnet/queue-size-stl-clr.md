---
title: "queue::size (STL/CLR) | Microsoft Docs"
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
  - "cliext::queue::size"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "size (miembro) [STL/CLR]"
ms.assetid: 864510ef-5a00-4377-b286-1e73f237e359
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# queue::size (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuenta el número de elementos.  
  
## Sintaxis  
  
```  
size_type size();  
```  
  
## Comentarios  
 La función miembro devuelve la longitud de la secuencia controlada.  Se utiliza para determinar el número de elementos actualmente en la secuencia controlada.  Si todo lo que se utiliza es de si la secuencia tiene un tamaño distinto de cero, vea [queue::empty](../dotnet/queue-empty-stl-clr.md)`()`.  
  
## Ejemplo  
  
```  
// cliext_queue_size.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());   
  
// pop an item and reinspect   
    c1.pop();   
    System::Console::WriteLine("size() = {0} after popping", c1.size());   
  
// add two elements and reinspect   
    c1.push(L'a');   
    c1.push(L'b');   
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());   
    return (0);   
    }  
  
```  
  
  **a b c**  
**size\(\) \= 3 que empiezan por 3**  
**size\(\) \= 2 después sacar**  
**size\(\) \= 4 después de agregar 2**   
## Requisitos  
 cliext \<\/cola de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [queue](../dotnet/queue-stl-clr.md)   
 [queue::empty](../dotnet/queue-empty-stl-clr.md)