---
title: "set::set (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::set::set"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "set (miembro) [STL/CLR]"
ms.assetid: 0cce8501-92ed-431c-b711-14e0b7be7375
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# set::set (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Construye un objeto contenedor.  
  
## Sintaxis  
  
```  
set();  
explicit set(key_compare^ pred);  
set(set<Key>% right);  
set(set<Key>^ right);  
template<typename InIter>  
    setset(InIter first, InIter last);  
template<typename InIter>  
    set(InIter first, InIter last,  
        key_compare^ pred);  
set(System::Collections::Generic::IEnumerable<GValue>^ right);  
set(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred);  
```  
  
#### Parámetros  
 first  
 Inicio del intervalo que se va a insertar.  
  
 last  
 Final del intervalo que se va a insertar.  
  
 pred  
 Ordenar el predicado de la secuencia controlada.  
  
 right  
 Objeto o intervalo para insertar.  
  
## Comentarios  
 El constructor:  
  
 `set();`  
  
 inicializa la secuencia controlada sin elementos, con el predicado de ordenación predeterminado `key_compare()`.  Se utiliza para especificar una secuencia controlada inicial vacía, con el predicado de ordenación predeterminado.  
  
 El constructor:  
  
 `explicit set(key_compare^ pred);`  
  
 inicializa la secuencia controlada sin elementos, con el predicado de ordenación `pred`.  Se utiliza para especificar una secuencia controlada inicial vacía, con el predicado de ordenación especificado.  
  
 El constructor:  
  
 `set(set<Key>% right);`  
  
 inicializa la secuencia controlada con la secuencia `[``right``.`[set::begin](../dotnet/set-begin-stl-clr.md)`(),` `right``.`[set::end](../dotnet/set-end-stl-clr.md)`())`, con el predicado de ordenación predeterminado.  Se utiliza para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto determinado `right`, con el predicado de ordenación predeterminado.  
  
 El constructor:  
  
 `set(set<Key>^ right);`  
  
 inicializa la secuencia controlada con la secuencia `[``right``->`[set::begin](../dotnet/set-begin-stl-clr.md)`(),` `right``->`[set::end](../dotnet/set-end-stl-clr.md)`())`, con el predicado de ordenación predeterminado.  Se utiliza para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto determinado `right`, con el predicado de ordenación predeterminado.  
  
 El constructor:  
  
 `template<typename InIter>`  
  
 `set(InIter first, InIter last);`  
  
 inicializa la secuencia controlada con la secuencia `[``first``,` `last``)`, con el predicado de ordenación predeterminado.  Se utiliza para hacer la secuencia controlada una copia de otra secuencia, con el predicado de ordenación predeterminado.  
  
 El constructor:  
  
 `template<typename InIter>`  
  
 `set(InIter first, InIter last,`  
  
 `key_compare^ pred);`  
  
 inicializa la secuencia controlada con la secuencia `[``first``,` `last``)`, con el predicado de ordenación `pred`.  Se utiliza para hacer la secuencia controlada una copia de otra secuencia, con el predicado de ordenación especificado.  
  
 El constructor:  
  
 `set(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 inicializa la secuencia controlada con la secuencia indicada por el enumerador `right`, con el predicado de ordenación predeterminado.  Se utiliza para hacer la secuencia controlada una copia de otra secuencia descrita por un enumerador, con el predicado de ordenación predeterminado.  
  
 El constructor:  
  
 `set(System::Collections::Generic::IEnumerable<Key>^ right,`  
  
 `key_compare^ pred);`  
  
 inicializa la secuencia controlada con la secuencia indicada por el enumerador `right`, con el predicado de ordenación `pred`.  Se utiliza para hacer la secuencia controlada una copia de otra secuencia descrita por un enumerador, con el predicado de ordenación especificado.  
  
## Ejemplo  
  
```  
// cliext_set_construct.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
// construct an empty container   
    Myset c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Myset c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Myset c3(c1.begin(), c1.end());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Myset c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Myset c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Myset c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,   
            cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c6)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct from a generic container   
    Myset c7(c4);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Myset c8(%c3);   
    for each (wchar_t elem in c8)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **size\(\) \= 0**  
 **a b c**  
**size\(\) \= 0**  
 **b a c**  
 **a b c**  
 **b a c**  
 **a b c**  
 **b a c**  
 **b a c**  
 **a b c**   
## Requisitos  
 cliext \<o conjunto de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [set](../dotnet/set-stl-clr.md)   
 [set::generic\_container](../dotnet/set-generic-container-stl-clr.md)   
 [set::operator\=](../dotnet/set-operator-assign-stl-clr.md)