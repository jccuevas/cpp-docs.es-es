---
title: "list::begin (STL/CLR) | Microsoft Docs"
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
  - "cliext::list::begin"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "begin (miembro) [STL/CLR]"
ms.assetid: 3431467b-951a-498a-af8d-50f631da1646
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# list::begin (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Designa el principio de la secuencia controlada.  
  
## Sintaxis  
  
```  
iterator begin();  
```  
  
## Comentarios  
 La función miembro devuelve un iterador de acceso aleatorio que señala el primer elemento de la secuencia controlada, o simplemente más allá del final de una secuencia vacía.  Se usa para obtener un iterador que designe el principio de la secuencia controlada, indicado por `current`, pero su estado puede cambiar si cambia la longitud de la secuencia controlada.  
  
## Ejemplo  
  
```  
// cliext_list_begin.cpp   
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
  
// inspect first two items   
    cliext::list<wchar_t>::iterator it = c1.begin();   
    System::Console::WriteLine("*begin() = {0}", *it);   
    System::Console::WriteLine("*++begin() = {0}", *++it);   
  
// alter first two items and reinspect   
    *--it = L'x';   
    *++it = L'y';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
**\*begin\(\) \= a**  
**\*\+\+begin\(\) \= b**  
 **c de la y x**   
## Requisitos  
 cliext \<de**Encabezado:** \/enumerado\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [list](../dotnet/list-stl-clr.md)   
 [list::end](../dotnet/list-end-stl-clr.md)   
 [list::front](../dotnet/list-front-stl-clr.md)   
 [list::front\_item](../dotnet/list-front-item-stl-clr.md)