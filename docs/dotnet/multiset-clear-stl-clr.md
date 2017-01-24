---
title: "multiset::clear (STL/CLR) | Microsoft Docs"
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
  - "cliext::multiset::clear"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clear (miembro) [STL/CLR]"
ms.assetid: 63c21716-fa08-47b9-b457-0b76052c5079
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# multiset::clear (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Quita todos los elementos.  
  
## Sintaxis  
  
```  
void clear();  
```  
  
## Comentarios  
 La función miembro llama eficazmente [multiset::erase](../dotnet/multiset-erase-stl-clr.md)`(` [multiset::begin](../dotnet/multiset-begin-stl-clr.md)`(),` [multiset::end](../dotnet/multiset-end-stl-clr.md)`())`.  Se utiliza para garantizar que la secuencia controlada está vacía.  
  
## Ejemplo  
  
```  
// cliext_multiset_clear.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// add elements and clear again   
    c1.insert(L'a');   
    c1.insert(L'b');   
  
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
  **a b c**  
**size\(\) \= 0**  
 **una b**  
**size\(\) \= 0**   
## Requisitos  
 cliext \<o conjunto de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [multiset](../dotnet/multiset-stl-clr.md)   
 [multiset::erase](../dotnet/multiset-erase-stl-clr.md)