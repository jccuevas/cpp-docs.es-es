---
title: "list::unique (STL/CLR) | Microsoft Docs"
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
  - "cliext::list::unique"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unique (miembro) [STL/CLR]"
ms.assetid: c3a29e4e-0ec1-4472-b050-7a9511037132
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# list::unique (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Quita los elementos adyacentes que superan una prueba especificada.  
  
## Sintaxis  
  
```  
void unique();  
template<typename Pred2>  
    void unique(Pred2 pred);  
```  
  
#### Parámetros  
 pred  
 Comparador de los pares de elemento.  
  
## Comentarios  
 La primera función miembro quita de la secuencia controlada \(desactivada\) cada elemento que comparar el igual al elemento anterior \-\- si el elemento `X` precede al elemento `Y` y `X == Y`, la función miembro quita `Y`.  Se utiliza para quitar todas menos una copia de cada subsequence de los elementos adyacentes que comparan el igual.  Tenga en cuenta que si la secuencia controlada está ordenada, por ejemplo llamando a [list::sort](../dotnet/list-sort-stl-clr.md)`()`, la función miembro permite solo elementos con valores únicos. \(Hence el nombre\).  
  
 La segunda función miembro se comporta igual que el primero, salvo que quita cada elemento `Y` que sigue un elemento `X` para el que `pred``(X, Y)`.  Se utiliza para quitar todas menos una copia de cada subsequence de los elementos adyacentes que satisfacen una función de predicado o se delega especificado.  Tenga en cuenta que si la secuencia controlada está ordenada, por ejemplo llamando a `sort(``pred``)`, la función miembro permite solo los elementos que no tienen equivalente de ordenación con ningún otro elemento.  
  
## Ejemplo  
  
```  
// cliext_list_unique.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display contents after unique   
    cliext::list<wchar_t> c2(c1);   
    c2.unique();   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display contents after unique(not_equal_to)   
    c2 = c1;   
    c2.unique(cliext::not_equal_to<wchar_t>());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **una b c**  
 **a b c**  
 **a**   
## Requisitos  
 cliext \<de**Encabezado:** \/enumerado\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [list](../dotnet/list-stl-clr.md)   
 [list::remove](../dotnet/list-remove-stl-clr.md)   
 [list::remove\_if](../dotnet/list-remove-if-stl-clr.md)   
 [list::sort](../dotnet/list-sort-stl-clr.md)