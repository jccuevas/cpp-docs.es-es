---
title: "list::swap (STL/CLR) | Microsoft Docs"
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
  - "cliext::list::swap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "swap (miembro) [STL/CLR]"
ms.assetid: 188b66c2-0a08-4001-a566-41d0955c89bd
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# list::swap (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Intercambia el contenido de dos contenedores.  
  
## Sintaxis  
  
```  
void swap(list<Value>% right);  
```  
  
#### Parámetros  
 right  
 Contenedor con el que se va a intercambiar el contenido.  
  
## Comentarios  
 La función miembro cambia las secuencias controladas entre `*this` y `right`.  Hacerlo en tiempo constante y no produce ninguna excepción.  Se utiliza como una manera rápida de cambiar el contenido de dos contenedores.  
  
## Ejemplo  
  
```  
// cliext_list_swap.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct another container with repetition of values   
    cliext::list<wchar_t> c2(5, L'x');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// swap and redisplay   
    c1.swap(c2);   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **x x x x x**  
 **x x x x x**  
 **a b c**   
## Requisitos  
 cliext \<de**Encabezado:** \/enumerado\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [list](../dotnet/list-stl-clr.md)   
 [list::assign](../dotnet/list-assign-stl-clr.md)   
 [list::operator\=](../dotnet/list-operator-assign-stl-clr.md)