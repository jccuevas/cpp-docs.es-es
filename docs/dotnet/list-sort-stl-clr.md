---
title: "list::sort (STL/CLR) | Microsoft Docs"
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
  - "cliext::list::sort"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sort (miembro) [STL/CLR]"
ms.assetid: f811d5f4-a19e-4194-8765-1e68097c52f0
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# list::sort (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Ordena la secuencia controlada.  
  
## Sintaxis  
  
```  
void sort();  
template<typename Pred2>  
    void sort(Pred2 pred);  
```  
  
#### Parámetros  
 pred  
 Comparador de los pares de elemento.  
  
## Comentarios  
 La primera función miembro reorganiza los elementos de la secuencia controlada de modo que no es de un `operator<` \-\- los elementos no disminuyen en valor a medida que avance por la secuencia.  Utiliza esta función miembro para ordenar la secuencia en sentido ascendente.  
  
 La segunda función miembro se comporta igual que el primero, salvo que la secuencia está ordenada por `pred` \-\- `pred``(X, Y)` es false para cualquier elemento `X` que siga el elemento `Y` en la secuencia resultante.  Se utiliza para ordenar la secuencia en un orden que se especifica por una función o un delegado de predicado.  
  
 Ambas funciones realizan una ordenación estable \-\- no es ningún par de elementos de la secuencia controlada original en la secuencia controlada resultante.  
  
## Ejemplo  
  
```  
// cliext_list_sort.cpp   
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
  
// sort descending and redisplay   
    c1.sort(cliext::greater<wchar_t>());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// sort ascending and redisplay   
    c1.sort();   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **b a c**  
 **a b c**   
## Requisitos  
 cliext \<de**Encabezado:** \/enumerado\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [list](../dotnet/list-stl-clr.md)   
 [list::merge](../dotnet/list-merge-stl-clr.md)   
 [list::reverse](../dotnet/list-reverse-stl-clr.md)   
 [list::splice](../dotnet/list-splice-stl-clr.md)   
 [list::unique](../dotnet/list-unique-stl-clr.md)