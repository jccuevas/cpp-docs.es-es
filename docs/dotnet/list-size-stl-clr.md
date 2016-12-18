---
title: "list::size (STL/CLR) | Microsoft Docs"
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
  - "cliext::list::size"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "size (miembro) [STL/CLR]"
ms.assetid: 409e39fb-4468-44bb-b179-52c90e2fa293
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# list::size (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuenta el número de elementos.  
  
## Sintaxis  
  
```  
size_type size();  
```  
  
## Comentarios  
 La función miembro devuelve la longitud de la secuencia controlada.  Se utiliza para determinar el número de elementos actualmente en la secuencia controlada.  Si todo lo que se utiliza es de si la secuencia tiene un tamaño distinto de cero, vea [list::empty](../dotnet/list-empty-stl-clr.md)`()`.  
  
## Ejemplo  
  
```  
// cliext_list_size.cpp   
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
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0} after clearing", c1.size());   
  
// add elements and clear again   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());   
    return (0);   
    }  
  
```  
  
  **a b c**  
**size\(\) \= 3 que empiezan por 3**  
**size\(\) \= 0 después de borrar**  
**size\(\) \= 2 después de agregar 2**   
## Requisitos  
 cliext \<de**Encabezado:** \/enumerado\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [list](../dotnet/list-stl-clr.md)   
 [list::empty](../dotnet/list-empty-stl-clr.md)