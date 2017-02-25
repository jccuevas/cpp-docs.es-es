---
title: "stack::assign (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::stack::assign"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "assign (miembro) [STL/CLR]"
ms.assetid: 18cc35ad-23cf-4a5a-adae-d967dc5d6980
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# stack::assign (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Reemplaza todos los elementos.  
  
## Sintaxis  
  
```  
void assign(stack<Value, Container>% right);  
```  
  
#### Parámetros  
 right  
 Adaptador de contenedor que se va a insertar.  
  
## Comentarios  
 La función miembro asigna `right``.get_container()` al contenedor subyacente.  Se utiliza para cambiar el contenido completo de la pila.  
  
## Ejemplo  
  
```  
// cliext_stack_assign.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign a repetition of values   
    Mystack c2;   
    c2.assign(c1);   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **a b c**   
## Requisitos  
 cliext \<\/pila de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [pila](../dotnet/stack-stl-clr.md)   
 [stack::operator\=](../dotnet/stack-operator-assign-stl-clr.md)