---
title: "hash_multiset::hash_multiset (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_multiset::hash_multiset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "hash_multiset (miembro) [STL/CLR]"
ms.assetid: 1b224c60-b714-4ed5-9234-79b61b92a953
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_multiset::hash_multiset (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Construye un objeto contenedor.  
  
## Sintaxis  
  
```  
hash_multiset();  
explicit hash_multiset(key_compare^ pred);  
hash_multiset(key_compare^ pred, hasher^ hashfn);  
hash_multiset(hash_multiset<Key>% right);  
hash_multiset(hash_multiset<Key>^ right);  
template<typename InIter>  
    hash_multiset(InIter first, InIter last);  
template<typename InIter>  
    hash_multiset(InIter first, InIter last,  
        key_compare^ pred);  
template<typename InIter>  
    hash_multiset(InIter first, InIter last,  
        key_compare^ pred, hasher^ hashfn);  
hash_multiset(System::Collections::Generic::IEnumerable<GValue>^ right);  
hash_multiset(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred);  
hash_multiset(System::Collections::Generic::IEnumerable<GValue>^ right,  
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
  
 `hash_multiset();`  
  
 inicializa la secuencia controlada sin elementos, con el predicado de ordenación predeterminado `key_compare()`, y con la función hash predeterminada.  Se utiliza para especificar una secuencia controlada inicial vacía, con el predicado y la función hash de ordenación predeterminados.  
  
 El constructor:  
  
 `explicit hash_multiset(key_compare^ pred);`  
  
 inicializa la secuencia controlada sin elementos, con el predicado de ordenación `pred`, y con la función hash predeterminada.  Se utiliza para especificar una secuencia controlada inicial vacía, con el predicado de ordenación especificado y la función hash predeterminada.  
  
 El constructor:  
  
 `hash_multiset(key_compare^ pred, hasher^ hashfn);`  
  
 inicializa la secuencia controlada sin elementos, con el predicado de ordenación `pred`, y con la función hash `hashfn`.  Se utiliza para especificar una secuencia controlada inicial vacía, con el predicado y la función hash de ordenación especificados.  
  
 El constructor:  
  
 `hash_multiset(hash_multiset<Key>% right);`  
  
 inicializa la secuencia controlada con la secuencia `[``right``.`[hash\_multiset::begin](../dotnet/hash-multiset-begin-stl-clr.md)`(),` `right``.`[hash\_multiset::end](../dotnet/hash-multiset-end-stl-clr.md)`())`, con el predicado de ordenación predeterminado, y con la función hash predeterminada.  Se utiliza para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto `right`de hash\_multiset, con el predicado y la función hash de ordenación predeterminados.  
  
 El constructor:  
  
 `hash_multiset(hash_multiset<Key>^ right);`  
  
 inicializa la secuencia controlada con la secuencia `[``right``->`[hash\_multiset::begin](../dotnet/hash-multiset-begin-stl-clr.md)`(),` `right``->`[hash\_multiset::end](../dotnet/hash-multiset-end-stl-clr.md)`())`, con el predicado de ordenación predeterminado, y con la función hash predeterminada.  Se utiliza para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto `right`de hash\_multiset, con el predicado y la función hash de ordenación predeterminados.  
  
 El constructor:  
  
 `template<typename InIter>`  
  
 `hash_multiset(InIter first, InIter last);`  
  
 inicializa la secuencia controlada con la secuencia `[``first``,` `last``)`, con el predicado de ordenación predeterminado, y con la función hash predeterminada.  Se utiliza para hacer la secuencia controlada una copia de otra secuencia, con el predicado y la función hash de ordenación predeterminados.  
  
 El constructor:  
  
 `template<typename InIter>`  
  
 `hash_multiset(InIter first, InIter last,`  
  
 `key_compare^ pred);`  
  
 inicializa la secuencia controlada con la secuencia `[``first``,` `last``)`, con el predicado de ordenación `pred`, y con la función hash predeterminada.  Se utiliza para hacer la secuencia controlada una copia de otra secuencia, con el predicado de ordenación especificado y la función hash predeterminada.  
  
 El constructor:  
  
 `template<typename InIter>`  
  
 `hash_multiset(InIter first, InIter last,`  
  
 `key_compare^ pred, hasher^ hashfn);`  
  
 inicializa la secuencia controlada con la secuencia `[``first``,` `last``)`, con el predicado de ordenación `pred`, y con la función hash `hashfn`.  Se utiliza para hacer la secuencia controlada una copia de otra secuencia, con el predicado y la función hash de ordenación especificados.  
  
 El constructor:  
  
 `hash_multiset(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 inicializa la secuencia controlada con la secuencia indicada por el enumerador `right`, con el predicado de ordenación predeterminado, y con la función hash predeterminada.  Se utiliza para hacer la secuencia controlada una copia de otra secuencia descrita por un enumerador, con el predicado y la función hash de ordenación predeterminados.  
  
 El constructor:  
  
 `hash_multiset(System::Collections::Generic::IEnumerable<Key>^ right,`  
  
 `key_compare^ pred);`  
  
 inicializa la secuencia controlada con la secuencia indicada por el enumerador `right`, con el predicado de ordenación `pred`, y con la función hash predeterminada.  Se utiliza para hacer la secuencia controlada una copia de otra secuencia descrita por un enumerador, con el predicado y la función hash especificados predeterminado de ordenación.  
  
 El constructor:  
  
 `hash_multiset(System::Collections::Generic::IEnumerable<Key>^ right,`  
  
 `key_compare^ pred, hasher^ hashfn);`  
  
 inicializa la secuencia controlada con la secuencia indicada por el enumerador `right`, con el predicado de ordenación `pred`, y con la función hash `hashfn`.  Se utiliza para hacer la secuencia controlada una copia de otra secuencia descrita por un enumerador, con el predicado y la función hash de ordenación especificados.  
  
## Ejemplo  
  
```  
// cliext_hash_multiset_construct.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
int myfun(wchar_t key)   
    { // hash a key   
    return (key ^ 0xdeadbeef);   
    }   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
// construct an empty container   
    Myhash_multiset c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Myhash_multiset c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule and hash function   
    Myhash_multiset c2h(cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_multiset::hasher(&myfun));   
    System::Console::WriteLine("size() = {0}", c2h.size());   
  
    c2h.insert(c1.begin(), c1.end());   
    for each (wchar_t elem in c2h)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Myhash_multiset c3(c1.begin(), c1.end());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Myhash_multiset c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule and hash function   
    Myhash_multiset c4h(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_multiset::hasher(&myfun));   
    for each (wchar_t elem in c4h)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Myhash_multiset c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Myhash_multiset c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,   
            cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c6)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule and hash function   
    Myhash_multiset c6h(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,   
            cliext::greater_equal<wchar_t>(),   
                gcnew Myhash_multiset::hasher(&myfun));   
    for each (wchar_t elem in c6h)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct from a generic container   
    Myhash_multiset c7(c4);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Myhash_multiset c8(%c3);   
    for each (wchar_t elem in c8)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **size\(\) \= 0**  
 **a b c**  
**size\(\) \= 0**  
 **a b c**  
**size\(\) \= 0**  
 **b a c**  
 **a b c**  
 **a b c**  
 **b a c**  
 **a b c**  
 **a b c**  
 **b a c**  
 **a b c**  
 **a b c**   
## Requisitos  
 cliext \<\/hash\_set de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_multiset::generic\_container](../dotnet/hash-multiset-generic-container-stl-clr.md)   
 [hash\_multiset::operator\=](../dotnet/hash-multiset-operator-assign-stl-clr.md)