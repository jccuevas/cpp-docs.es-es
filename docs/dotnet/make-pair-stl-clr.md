---
title: "make_pair (STL/CLR) | Microsoft Docs"
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
  - "cliext::make_pair"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "make_pair (función) [STL/CLR]"
ms.assetid: 74733f2c-97b0-4d69-b431-5ab8f0de9e3e
caps.latest.revision: 8
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# make_pair (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cree `pair` de un par de valores.  
  
## Sintaxis  
  
```  
template<typename Value1,  
    typename Value2>  
    pair<Value1, Value2> make_pair(Value1 first, Value2 second);  
```  
  
#### Parámetros  
 Value1  
 El tipo del primer valor ajustado.  
  
 Value2  
 El tipo del segundo valor ajustado.  
  
 first  
 Primer valor a ajustar.  
  
 second  
 Segundo valor a ajustar.  
  
## Comentarios  
 La función de la plantilla devuelve `pair<``Value1``,` `Value2``>(``first``,` `second``)`.  Se utiliza para construir un objeto de `pair``<``Value1``,` `Value2``>` de un par de valores.  
  
## Ejemplo  
  
```  
// cliext_make_pair.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
  
    c1 = cliext::make_pair(L'y', 4);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
    return (0);   
    }  
  
```  
  
  **\[x, 3\]**  
**\[y, 4\]**   
## Requisitos  
 cliext \<\/utilidad de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [range\_adapter](../dotnet/range-adapter-stl-clr.md)