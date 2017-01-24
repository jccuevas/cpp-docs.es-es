---
title: "queue::assign (STL/CLR) | Microsoft Docs"
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
  - "cliext::queue::assign"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "assign (miembro) [STL/CLR]"
ms.assetid: 5bec8a84-9561-43f7-ad7f-f845d0edef41
caps.latest.revision: 14
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# queue::assign (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Reemplaza todos los elementos.  
  
## Sintaxis  
  
```  
void assign(queue<Value, Container>% right);  
```  
  
#### Parámetros  
 right  
 Adaptador de contenedor que se va a insertar.  
  
## Comentarios  
 La función miembro asigna `right``.get_container()` al contenedor subyacente.  Se utiliza para cambiar el contenido completo de la cola.  
  
## Ejemplo  
  
```  
// cliext_queue_assign.cpp   
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
  
// assign a repetition of values   
    Myqueue c2;   
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
 cliext \<\/cola de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [queue](../dotnet/queue-stl-clr.md)   
 [queue::operator\=](../dotnet/queue-operator-assign-stl-clr.md)