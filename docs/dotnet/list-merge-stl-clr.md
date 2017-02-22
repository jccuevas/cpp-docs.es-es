---
title: "list::merge (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::list::merge"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "merge (miembro) [STL/CLR]"
ms.assetid: f8e93cd3-bd08-4086-859b-08a2899cc9a6
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# list::merge (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Combina dos secuencias controladas ordenadas.  
  
## Sintaxis  
  
```  
void merge(list<Value>% right);  
template<typename Pred2>  
    void merge(list<Value>% right, Pred2 pred);  
```  
  
#### Parámetros  
 pred  
 Comparador de los pares de elemento.  
  
 right  
 Contenedor para combinar en.  
  
## Comentarios  
 La primera función miembro quita todos los elementos de la secuencia controlada por `right` y los inserta en la secuencia controlada.  Las dos secuencias se deben ordenar previamente por `operator<` \-\- los elementos no debe disminuir en valor a medida que avance con cualquier secuencia.  La secuencia resultante también está ordenada por `operator<`.  Utiliza esta función miembro para combinar dos secuencias ese aumento de valor en una secuencia que también aumenta en valor.  
  
 La segunda función miembro se comporta igual que el primero, salvo que las secuencias se ordenan por `pred` \-\- `pred``(X, Y)` debe ser false para cualquier elemento `X` que siga el elemento `Y` en la secuencia.  Se utiliza para combinar dos secuencias ordenadas por una función de predicado o para delegarlas especificado.  
  
 Ambas funciones realizan una combinación estable \-\- no es ningún par de elementos en ninguna de las secuencias controladas originales en la secuencia controlada resultante.  Además, si un par de elementos `X` y `Y` en la secuencia controlada resultante tiene el orden equivalente \-\- `!(X < Y) && !(X < Y)` \-\- un elemento de la secuencia controlada original aparece antes de un elemento de la secuencia controlada por `right`.  
  
## Ejemplo  
  
```  
// cliext_list_merge.cpp   
// compile with: /clr   
#include <cliext/list>   
  
typedef cliext::list<wchar_t> Mylist;   
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'c');   
    c1.push_back(L'e');   
  
// display initial contents " a c e"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    cliext::list<wchar_t> c2;   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
    c2.push_back(L'f');   
  
// display initial contents " b d f"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// merge and display   
    cliext::list<wchar_t> c3(c1);   
    c3.merge(c2);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("c2.size() = {0}", c2.size());   
  
// sort descending, merge descending, and redisplay   
    c1.sort(cliext::greater<wchar_t>());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    c3.sort(cliext::greater<wchar_t>());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    c3.merge(c1, cliext::greater<wchar_t>());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("c1.size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
  **C. e**  
 **f de d b**  
 **a b c d e f**  
**c2.size\(\) \= 0**  
 **Comunidad Europea a**  
 **b a c de d de f e**  
 **b c c de d de f e e a**  
**c1.size\(\) \= 0**   
## Requisitos  
 cliext \<de**Encabezado:** \/enumerado\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [list](../dotnet/list-stl-clr.md)   
 [list::sort](../dotnet/list-sort-stl-clr.md)   
 [list::splice](../dotnet/list-splice-stl-clr.md)