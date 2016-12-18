---
title: "operator== (vector) (STL/CLR) | Microsoft Docs"
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
  - "cliext::vector::operator=="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator== (miembro) [STL/CLR]"
ms.assetid: b552c9a1-8d06-4090-b394-d08a84947594
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# operator== (vector) (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comparación igual vectoriales.  
  
## Sintaxis  
  
```  
template<typename Value>  
    bool operator==(vector<Value>% left,  
        vector<Value>% right);  
```  
  
#### Parámetros  
 left  
 Contenedor izquierdo a comparar.  
  
 right  
 Contenedor derecho a comparar.  
  
## Comentarios  
 La función de operador devuelve true solo si las secuencias controladas por `left` y `right` tienen la misma longitud y, para cada posición `i`, `left``[i] ==` `right``[i]`.  Se utiliza para probar si `left` se le igual que `right` cuando los dos vectores son elemento comparado al lado de elemento.  
  
## Ejemplo  
  
```  
// cliext_vector_operator_eq.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::vector<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] == [a b c] is {0}",   
        c1 == c1);   
    System::Console::WriteLine("[a b c] == [a b d] is {0}",   
        c1 == c2);   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **una d b**  
**\=\= \[de una b c\] \[una b c\] es True**  
**\=\= \[de una b c\] \[una d b\] es False**   
## Requisitos  
 cliext \<\/vector de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [vector](../dotnet/vector-stl-clr.md)   
 [operator\!\= \(vector\)](../dotnet/operator-inequality-vector-stl-clr.md)   
 [operator\< \(vector\)](../dotnet/operator-less-than-vector-stl-clr.md)   
 [operator\>\= \(vector\)](../dotnet/operator-greater-or-equal-vector-stl-clr.md)   
 [operator\> \(vector\)](../dotnet/operator-greater-than-vector-stl-clr.md)   
 [operator\<\= \(vector\)](../dotnet/operator-less-or-equal-vector-stl-clr.md)