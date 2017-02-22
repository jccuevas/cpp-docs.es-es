---
title: "hash_multimap::hash_multimap (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::hash_multimap::hash_multimap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "hash_multimap (miembro) [STL/CLR]"
ms.assetid: a1d576a7-5dc7-4ad9-abef-ee7a13caaec3
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# hash_multimap::hash_multimap (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Construye un objeto contenedor.  
  
## Sintaxis  
  
```  
hash_multimap();  
explicit hash_multimap(key_compare^ pred);  
hash_multimap(key_compare^ pred, hasher^ hashfn);  
hash_multimap(hash_multimap<Key, Mapped>% right);  
hash_multimap(hash_multimap<Key, Mapped>^ right);  
template<typename InIter>  
    hash_multimaphash_multimap(InIter first, InIter last);  
template<typename InIter>  
    hash_multimap(InIter first, InIter last,  
        key_compare^ pred);  
template<typename InIter>  
    hash_multimap(InIter first, InIter last,  
        key_compare^ pred, hasher^ hashfn);  
hash_multimap(System::Collections::Generic::IEnumerable<GValue>^ right);  
hash_multimap(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred);  
hash_multimap(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred, hasher^ hashfn);  
```  
  
#### Parámetros  
 first  
 Inicio del intervalo que se va a insertar.  
  
 hashfn  
 Función hash para asignar teclas a los depósitos.  
  
 last  
 Final del intervalo que se va a insertar.  
  
 pred  
 Ordenar el predicado de la secuencia controlada.  
  
 right  
 Objeto o intervalo para insertar.  
  
## Comentarios  
 El constructor:  
  
 `hash_multimap();`  
  
 inicializa la secuencia controlada sin elementos, con el predicado de ordenación predeterminado `key_compare()`, y con la función hash predeterminada.  Se utiliza para especificar una secuencia controlada inicial vacía, con el predicado y la función hash de ordenación predeterminados.  
  
 El constructor:  
  
 `explicit hash_multimap(key_compare^ pred);`  
  
 inicializa la secuencia controlada sin elementos, con el predicado de ordenación `pred`, y con la función hash predeterminada.  Se utiliza para especificar una secuencia controlada inicial vacía, con el predicado de ordenación especificado y la función hash predeterminada.  
  
 El constructor:  
  
 `hash_multimap(key_compare^ pred, hasher^ hashfn);`  
  
 inicializa la secuencia controlada sin elementos, con el predicado de ordenación `pred`, y con la función hash `hashfn`.  Se utiliza para especificar una secuencia controlada inicial vacía, con el predicado y la función hash de ordenación especificados.  
  
 El constructor:  
  
 `hash_multimap(hash_multimap<Key, Mapped>% right);`  
  
 inicializa la secuencia controlada con la secuencia `[``right``.`[hash\_multimap::begin](../dotnet/hash-multimap-begin-stl-clr.md)`(),` `right``.`[hash\_multimap::end](../dotnet/hash-multimap-end-stl-clr.md)`())`, con el predicado de ordenación predeterminado, y con la función hash predeterminada.  Se utiliza para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto `right`de hash\_multimap, con el predicado y la función hash de ordenación predeterminados.  
  
 El constructor:  
  
 `hash_multimap(hash_multimap<Key, Mapped>^ right);`  
  
 inicializa la secuencia controlada con la secuencia `[``right``->`[hash\_multimap::begin](../dotnet/hash-multimap-begin-stl-clr.md)`(),` `right``->`[hash\_multimap::end](../dotnet/hash-multimap-end-stl-clr.md)`())`, con el predicado de ordenación predeterminado, y con la función hash predeterminada.  Se utiliza para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto `right`de hash\_multimap, con el predicado y la función hash de ordenación predeterminados.  
  
 El constructor:  
  
 `template<typename InIter>`  
  
 `hash_multimap(InIter first, InIter last);`  
  
 inicializa la secuencia controlada con la secuencia `[``first``,` `last``)`, con el predicado de ordenación predeterminado, y con la función hash predeterminada.  Se utiliza para hacer la secuencia controlada una copia de otra secuencia, con el predicado y la función hash de ordenación predeterminados.  
  
 El constructor:  
  
 `template<typename InIter>`  
  
 `hash_multimap(InIter first, InIter last,`  
  
 `key_compare^ pred);`  
  
 inicializa la secuencia controlada con la secuencia `[``first``,` `last``)`, con el predicado de ordenación `pred`, y con la función hash predeterminada.  Se utiliza para hacer la secuencia controlada una copia de otra secuencia, con el predicado de ordenación especificado y la función hash predeterminada.  
  
 El constructor:  
  
 `template<typename InIter>`  
  
 `hash_multimap(InIter first, InIter last,`  
  
 `key_compare^ pred, hasher^ hashfn);`  
  
 inicializa la secuencia controlada con la secuencia `[``first``,` `last``)`, con el predicado de ordenación `pred`, y con la función hash `hashfn`.  Se utiliza para hacer la secuencia controlada una copia de otra secuencia, con el predicado y la función hash de ordenación especificados.  
  
 El constructor:  
  
 `hash_multimap(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 inicializa la secuencia controlada con la secuencia indicada por el enumerador `right`, con el predicado de ordenación predeterminado, y con la función hash predeterminada.  Se utiliza para hacer la secuencia controlada una copia de otra secuencia descrita por un enumerador, con el predicado y la función hash de ordenación predeterminados.  
  
 El constructor:  
  
 `hash_multimap(System::Collections::Generic::IEnumerable<Key>^ right,`  
  
 `key_compare^ pred);`  
  
 inicializa la secuencia controlada con la secuencia indicada por el enumerador `right`, con el predicado de ordenación `pred`, y con la función hash predeterminada.  Se utiliza para hacer la secuencia controlada una copia de otra secuencia descrita por un enumerador, con el predicado y la función hash especificados predeterminado de ordenación.  
  
 El constructor:  
  
 `hash_multimap(System::Collections::Generic::IEnumerable<Key>^ right,`  
  
 `key_compare^ pred, hasher^ hashfn);`  
  
 inicializa la secuencia controlada con la secuencia indicada por el enumerador `right`, con el predicado de ordenación `pred`, y con la función hash `hashfn`.  Se utiliza para hacer la secuencia controlada una copia de otra secuencia descrita por un enumerador, con el predicado y la función hash de ordenación especificados.  
  
## Ejemplo  
  
```  
// cliext_hash_multimap_construct.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
int myfun(wchar_t key)   
    { // hash a key   
    return (key ^ 0xdeadbeef);   
    }   
  
typedef cliext::hash_multimap<wchar_t, int> Myhash_multimap;   
int main()   
    {   
// construct an empty container   
    Myhash_multimap c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(Myhash_multimap::make_value(L'a', 1));   
    c1.insert(Myhash_multimap::make_value(L'b', 2));   
    c1.insert(Myhash_multimap::make_value(L'c', 3));   
    for each (Myhash_multimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Myhash_multimap c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (Myhash_multimap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an ordering rule and hash function   
    Myhash_multimap c2h(cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_multimap::hasher(&myfun));   
    System::Console::WriteLine("size() = {0}", c2h.size());   
  
    c2h.insert(c1.begin(), c1.end());   
    for each (Myhash_multimap::value_type elem in c2h)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Myhash_multimap c3(c1.begin(), c1.end());   
    for each (Myhash_multimap::value_type elem in c3)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Myhash_multimap c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (Myhash_multimap::value_type elem in c4)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule and hash function   
    Myhash_multimap c4h(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_multimap::hasher(&myfun));   
    for each (Myhash_multimap::value_type elem in c4h)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Myhash_multimap c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Myhash_multimap::value_type>^)%c3);   
    for each (Myhash_multimap::value_type elem in c5)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Myhash_multimap c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Myhash_multimap::value_type>^)%c3,   
                cliext::greater_equal<wchar_t>());   
    for each (Myhash_multimap::value_type elem in c6)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule and hash function   
    Myhash_multimap c6h(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Myhash_multimap::value_type>^)%c3,   
                cliext::greater_equal<wchar_t>(),   
                gcnew Myhash_multimap::hasher(&myfun));   
    for each (Myhash_multimap::value_type elem in c6h)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Myhash_multimap c7(c4);   
    for each (Myhash_multimap::value_type elem in c7)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    Myhash_multimap c8(%c3);   
    for each (Myhash_multimap::value_type elem in c8)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **size\(\) \= 0**  
 **\[un 1\] \[b 2\] \[c 3\]**  
**size\(\) \= 0**  
 **\[un 1\] \[b 2\] \[c 3\]**  
**size\(\) \= 0**  
 **\[c 3\] \[b 2\] \[un 1\]**  
 **\[un 1\] \[b 2\] \[c 3\]**  
 **\[un 1\] \[b 2\] \[c 3\]**  
 **\[c 3\] \[b 2\] \[un 1\]**  
 **\[un 1\] \[b 2\] \[c 3\]**  
 **\[un 1\] \[b 2\] \[c 3\]**  
 **\[c 3\] \[b 2\] \[un 1\]**  
 **\[un 1\] \[b 2\] \[c 3\]**  
 **\[un 1\] \[b 2\] \[c 3\]**   
## Requisitos  
 cliext \<\/hash\_map de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [hash\_multimap](../dotnet/hash-multimap-stl-clr.md)   
 [hash\_multimap::generic\_container](../dotnet/hash-multimap-generic-container-stl-clr.md)   
 [hash\_multimap::operator\=](../dotnet/hash-multimap-operator-assign-stl-clr.md)