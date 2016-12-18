---
title: "stack::stack (STL/CLR) | Microsoft Docs"
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
  - "cliext::stack::stack"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "stack (miembro) [STL/CLR]"
ms.assetid: f1cfb3fe-4d22-41e5-906b-e8faa0bcde9b
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# stack::stack (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Construye un objeto de adaptador de contenedor.  
  
## Sintaxis  
  
```  
stack();  
stack(stack<Value, Container>% right);  
stack(stack<Value, Container>^ right);  
explicit stack(container_type% wrapped);  
```  
  
#### Parámetros  
 right  
 Objeto a la copia.  
  
 ajustado  
 Contenedor ajustado a utilizar.  
  
## Comentarios  
 El constructor:  
  
 `stack();`  
  
 crea un contenedor ajustado vacío.  Se utiliza para especificar una secuencia controlada inicial vacía.  
  
 El constructor:  
  
 `stack(stack<Value, Container>% right);`  
  
 crea un contenedor ajustado que es una copia de `right.get_container()`.  Se utiliza para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto `right`de la pila.  
  
 El constructor:  
  
 `stack(stack<Value, Container>^ right);`  
  
 crea un contenedor ajustado que es una copia de `right->get_container()`.  Se utiliza para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto `*right`de la pila.  
  
 El constructor:  
  
 `explicit stack(container_type% wrapped);`  
  
 utilice el contenedor existente `wrapped` como contenedor ajustado.  Se utiliza para construir una pila de un contenedor existente.  
  
## Ejemplo  
  
```  
// cliext_stack_construct.cpp   
// compile with: /clr   
#include <cliext/stack>   
#include <cliext/vector>   
  
typedef cliext::stack<wchar_t> Mystack;   
typedef cliext::vector<wchar_t> Myvector;   
typedef cliext::stack<wchar_t, Myvector> Mystack_vec;   
int main()   
    {   
// construct an empty container   
    Mystack c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct from an underlying container   
    Myvector v2(5, L'x');   
    Mystack_vec c2(v2);       
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mystack_vec c3(c2);   
    for each (wchar_t elem in c3.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container through handle   
    Mystack_vec c4(%c2);   
    for each (wchar_t elem in c4.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **size\(\) \= 0**  
 **x x x x x**  
 **x x x x x**  
 **x x x x x**   
## Requisitos  
 cliext \<\/pila de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [pila](../dotnet/stack-stl-clr.md)   
 [stack::assign](../dotnet/stack-assign-stl-clr.md)   
 [stack::generic\_container](../dotnet/stack-generic-container-stl-clr.md)   
 [stack::operator\=](../dotnet/stack-operator-assign-stl-clr.md)