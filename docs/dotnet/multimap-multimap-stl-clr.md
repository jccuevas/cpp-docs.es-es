---
title: "multimap::multimap (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::multimap::multimap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "multimap (miembro) [STL/CLR]"
ms.assetid: cdf9c5dc-774c-424e-aeea-7554643e401c
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# multimap::multimap (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Construye un objeto contenedor.  
  
## Sintaxis  
  
```  
multimap();  
explicit multimap(key_compare^ pred);  
multimap(multimap<Key, Mapped>% right);  
multimap(multimap<Key, Mapped>^ right);  
template<typename InIter>  
    multimapmultimap(InIter first, InIter last);  
template<typename InIter>  
    multimap(InIter first, InIter last,  
        key_compare^ pred);  
multimap(System::Collections::Generic::IEnumerable<GValue>^ right);  
multimap(System::Collections::Generic::IEnumerable<GValue>^ right,  
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
  
 `multimap();`  
  
 inicializa la secuencia controlada sin elementos, con el predicado de ordenación predeterminado `key_compare()`.  Se utiliza para especificar una secuencia controlada inicial vacía, con el predicado de ordenación predeterminado.  
  
 El constructor:  
  
 `explicit multimap(key_compare^ pred);`  
  
 inicializa la secuencia controlada sin elementos, con el predicado de ordenación `pred`.  Se utiliza para especificar una secuencia controlada inicial vacía, con el predicado de ordenación especificado.  
  
 El constructor:  
  
 `multimap(multimap<Key, Mapped>% right);`  
  
 inicializa la secuencia controlada con la secuencia `[``right``.`[multimap::begin](../dotnet/multimap-begin-stl-clr.md)`(),` `right``.`[multimap::end](../dotnet/multimap-end-stl-clr.md)`())`, con el predicado de ordenación predeterminado.  Se utiliza para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto `right`de multimap, con el predicado de ordenación predeterminado.  
  
 El constructor:  
  
 `multimap(multimap<Key, Mapped>^ right);`  
  
 inicializa la secuencia controlada con la secuencia `[``right``->`[multimap::begin](../dotnet/multimap-begin-stl-clr.md)`(),` `right``->`[multimap::end](../dotnet/multimap-end-stl-clr.md)`())`, con el predicado de ordenación predeterminado.  Se utiliza para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto `right`de multimap, con el predicado de ordenación predeterminado.  
  
 El constructor:  
  
 `template<typename InIter>`  
  
 `multimap(InIter first, InIter last);`  
  
 inicializa la secuencia controlada con la secuencia `[``first``,` `last``)`, con el predicado de ordenación predeterminado.  Se utiliza para hacer la secuencia controlada una copia de otra secuencia, con el predicado de ordenación predeterminado.  
  
 El constructor:  
  
 `template<typename InIter>`  
  
 `multimap(InIter first, InIter last,`  
  
 `key_compare^ pred);`  
  
 inicializa la secuencia controlada con la secuencia `[``first``,` `last``)`, con el predicado de ordenación `pred`.  Se utiliza para hacer la secuencia controlada una copia de otra secuencia, con el predicado de ordenación especificado.  
  
 El constructor:  
  
 `multimap(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 inicializa la secuencia controlada con la secuencia indicada por el enumerador `right`, con el predicado de ordenación predeterminado.  Se utiliza para hacer la secuencia controlada una copia de otra secuencia descrita por un enumerador, con el predicado de ordenación predeterminado.  
  
 El constructor:  
  
 `multimap(System::Collections::Generic::IEnumerable<Key>^ right,`  
  
 `key_compare^ pred);`  
  
 inicializa la secuencia controlada con la secuencia indicada por el enumerador `right`, con el predicado de ordenación `pred`.  Se utiliza para hacer la secuencia controlada una copia de otra secuencia descrita por un enumerador, con el predicado de ordenación especificado.  
  
## Ejemplo  
  
```  
// cliext_multimap_construct.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::multimap<wchar_t, int> Mymultimap;   
int main()   
    {   
// construct an empty container   
    Mymultimap c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(Mymultimap::make_value(L'a', 1));   
    c1.insert(Mymultimap::make_value(L'b', 2));   
    c1.insert(Mymultimap::make_value(L'c', 3));   
    for each (Mymultimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Mymultimap c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (Mymultimap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Mymultimap c3(c1.begin(), c1.end());   
    for each (Mymultimap::value_type elem in c3)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Mymultimap c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (Mymultimap::value_type elem in c4)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Mymultimap c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Mymultimap::value_type>^)%c3);   
    for each (Mymultimap::value_type elem in c5)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Mymultimap c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Mymultimap::value_type>^)%c3,   
                cliext::greater_equal<wchar_t>());   
    for each (Mymultimap::value_type elem in c6)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mymultimap c7(c4);   
    for each (Mymultimap::value_type elem in c7)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    Mymultimap c8(%c3);   
    for each (Mymultimap::value_type elem in c8)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **size\(\) \= 0**  
 **\[un 1\] \[b 2\] \[c 3\]**  
**size\(\) \= 0**  
 **\[c 3\] \[b 2\] \[un 1\]**  
 **\[un 1\] \[b 2\] \[c 3\]**  
 **\[c 3\] \[b 2\] \[un 1\]**  
 **\[un 1\] \[b 2\] \[c 3\]**  
 **\[c 3\] \[b 2\] \[un 1\]**  
 **\[c 3\] \[b 2\] \[un 1\]**  
 **\[un 1\] \[b 2\] \[c 3\]**   
## Requisitos  
 cliext \<de**Encabezado:** \/asignado\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [multimap](../dotnet/multimap-stl-clr.md)   
 [multimap::generic\_container](../dotnet/multimap-generic-container-stl-clr.md)   
 [multimap::operator\=](../dotnet/multimap-operator-assign-stl-clr.md)