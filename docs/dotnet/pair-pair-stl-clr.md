---
title: "pair::pair (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::pair::pair"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "pair (miembro) [STL/CLR]"
ms.assetid: 188035f3-bd37-4b46-96dd-5ceb9a16df79
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# pair::pair (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Construye un objeto de pares.  
  
## Sintaxis  
  
```  
pair();  
pair(pair<Coll>% right);  
pair(pair<Coll>^ right);  
pair(Value1 val1, Value2 val2);  
```  
  
#### Parámetros  
 right  
 Pares a almacenar.  
  
 val1  
 Primer valor a almacenar.  
  
 val2  
 Segundo valor a almacenar.  
  
## Comentarios  
 El constructor:  
  
 `pair();`  
  
 inicializa el par almacenado con valores construidos predeterminado.  
  
 El constructor:  
  
 `pair(pair<Value1, Value2>% right);`  
  
 inicializa el par almacenado con `right``.`[pair::first](../dotnet/pair-first-stl-clr.md) y `right``.`[pair::second](../dotnet/pair-second-stl-clr.md).  
  
 `pair(pair<Value1, Value2>^ right);`  
  
 inicializa el par almacenado con `right``->`[pair::first](../dotnet/pair-first-stl-clr.md) y `right``>`[pair::second](../dotnet/pair-second-stl-clr.md).  
  
 El constructor:  
  
 `pair(Value1 val1, Value2 val2);`  
  
 inicializa el par almacenado con `val1` y `val2`.  
  
## Ejemplo  
  
```  
// cliext_pair_construct.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
// construct an empty container   
    cliext::pair<wchar_t, int> c1;   
    System::Console::WriteLine("[{0}, {1}]",   
        c1.first == L'\0' ? "\\0" : "??", c1.second);   
  
// construct with a pair of values   
    cliext::pair<wchar_t, int> c2(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
  
// construct by copying another pair   
    cliext::pair<wchar_t, int> c3(c2);   
    System::Console::WriteLine("[{0}, {1}]", c3.first, c3.second);   
  
// construct by copying a pair handle   
    cliext::pair<wchar_t, int> c4(%c3);   
    System::Console::WriteLine("[{0}, {1}]", c4.first, c4.second);   
  
    return (0);   
    }  
  
```  
  
  **\[\\0, 0\]**  
**\[x, 3\]**  
**\[x, 3\]**  
**\[x, 3\]**   
## Requisitos  
 cliext \<\/utilidad de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [pair](../dotnet/pair-stl-clr.md)