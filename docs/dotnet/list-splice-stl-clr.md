---
title: "list::splice (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::list::splice"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "splice (miembro) [STL/CLR]"
ms.assetid: ebc424b9-8341-4a88-b101-86d56324f5ac
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# list::splice (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Vínculos de Restitch entre nodos.  
  
## Sintaxis  
  
```  
void splice(iterator where, list<Value>% right);  
void splice(iterator where, list<Value>% right,  
    iterator first);  
void splice(iterator where, list<Value>% right,  
    iterator first, iterator last);  
```  
  
#### Parámetros  
 first  
 Inicio del intervalo a insertar.  
  
 last  
 Final del intervalo a insertar.  
  
 right  
 Contenedor a insertar de.  
  
 donde  
 Donde en el contenedor insertar antes.  
  
## Comentarios  
 La primera función miembro inserta la secuencia controlada por `right` antes del elemento de la secuencia controlada designada por a `where`.  También quita todos los elementos de `right`. \(`%``right` no debe ser igual a `this`.\) Se utiliza para insertar todo el una lista en otro.  
  
 La segunda función miembro quita el elemento indicada por `first` en la secuencia controlada por `right` y se inserta antes del elemento de la secuencia controlada designada por a `where`. \(Si `where` `==` `first` `||` `where` `== ++``first`, no se produce ningún cambio.\) Se utiliza para insertar un único elemento de una lista en otro.  
  
 La tercera función miembro inserta el subrango designado por `[``first``,` `last``)` de la secuencia controlada por `right` antes del elemento de la secuencia controlada designada por a `where`.  También quita el subrango original de la secuencia controlada por `right`. \(Si `right` `==` `this`, el intervalo `[``first``,` `last``)` no debe incluir el elemento indicada por `where`.\) Se utiliza para insertar un subsequence de cero o más elementos a partir de una lista de otro.  
  
## Ejemplo  
  
```  
// cliext_list_splice.cpp   
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
  
// splice to a new list   
    cliext::list<wchar_t> c2;   
    c2.splice(c2.begin(), c1);   
    System::Console::WriteLine("c1.size() = {0}", c1.size());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// return one element   
    c1.splice(c1.end(), c2, c2.begin());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// return remaining elements   
    c1.splice(c1.begin(), c2, c2.begin(), c2.end());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("c2.size() = {0}", c2.size());   
    return (0);   
    }  
  
```  
  
  **a b c**  
**c1.size\(\) \= 0**  
 **a b c**  
 **a**  
 **b c**  
 **c a b**  
**c2.size\(\) \= 0**   
## Requisitos  
 cliext \<de**Encabezado:** \/enumerado\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [list](../dotnet/list-stl-clr.md)   
 [list::assign](../dotnet/list-assign-stl-clr.md)   
 [list::insert](../dotnet/list-insert-stl-clr.md)   
 [list::merge](../dotnet/list-merge-stl-clr.md)