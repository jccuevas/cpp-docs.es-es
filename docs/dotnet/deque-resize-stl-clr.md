---
title: "deque::resize (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::deque::resize"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "resize (miembro) [STL/CLR]"
ms.assetid: c83f3c57-38b3-4706-a124-59bafbf88484
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# deque::resize (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cambia el número de elementos.  
  
## Sintaxis  
  
```  
void resize(size_type new_size);  
void resize(size_type new_size, value_type val);  
```  
  
#### Parámetros  
 new\_size  
 Nuevo tamaño de la secuencia controlada.  
  
 val  
 Valor del elemento de relleno.  
  
## Comentarios  
 Las funciones miembro ambos asegurarse de que [deque::size](../dotnet/deque-size-stl-clr.md)`()` en adelante devuelve `new_size`.  Si debe crear la secuencia controlada más larga, la primera función miembro anexa elementos con el valor `value_type()`, mientras que la segunda función miembro anexa elementos con el valor `val`.  Para crear la secuencia controlada más corta, ambas funciones miembro desactive eficazmente los tiempos pasan de [deque::size](../dotnet/deque-size-stl-clr.md)`() -` `new_size` del elemento.  Se utiliza para garantizar que la secuencia controlada tiene un tamaño `new_size`, por la reducción o el relleno la secuencia controlada actual.  
  
## Ejemplo  
  
```  
// cliext_deque_resize.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
// construct an empty container and pad with default values   
    cliext::deque<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
    c1.resize(4);   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// resize to empty   
    c1.resize(0);   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// resize and pad   
    c1.resize(5, L'x');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **size\(\) \= 0**  
 **0 0 0 0**  
**size\(\) \= 0**  
 **x x x x x**   
## Requisitos  
 **Encabezado:** \<cliext\/deque\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [deque](../dotnet/deque-stl-clr.md)   
 [deque::clear](../dotnet/deque-clear-stl-clr.md)   
 [deque::erase](../dotnet/deque-erase-stl-clr.md)   
 [deque::insert](../dotnet/deque-insert-stl-clr.md)