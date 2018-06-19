---
title: 'hash_multiset:: hash_multiset (STL/CLR) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_multiset::hash_multiset
dev_langs:
- C++
helpviewer_keywords:
- hash_multiset member [STL/CLR]
ms.assetid: 1b224c60-b714-4ed5-9234-79b61b92a953
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 81006e74b98e3bce7a001489723e480f289b6a0a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33136326"
---
# <a name="hashmultisethashmultiset-stlclr"></a>hash_multiset::hash_multiset (STL/CLR)
Construye un objeto contenedor.  
  
## <a name="syntax"></a>Sintaxis  
  
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
  
#### <a name="parameters"></a>Parámetros  
 first  
 Comienzo del intervalo que se va a insertar.  
  
 hashfn  
 Función para las claves de asignación a depósitos de hash.  
  
 last  
 Final del intervalo que se va a insertar.  
  
 pred  
 Orden de predicado de la secuencia controlada.  
  
 right  
 Objeto o intervalo que se va a insertar.  
  
## <a name="remarks"></a>Comentarios  
 El constructor:  
  
 `hash_multiset();`  
  
 Inicializa la secuencia controlada con ningún elemento con el predicado del orden predeterminado `key_compare()`y con la función hash predeterminada. Se usa para especificar una secuencia controlada inicial vacía, con la función de predicado y hash del orden predeterminado.  
  
 El constructor:  
  
 `explicit hash_multiset(key_compare^ pred);`  
  
 Inicializa la secuencia controlada con ningún elemento con el predicado ordenación `pred`y con la función hash predeterminada. Se usa para especificar una secuencia controlada inicial vacía, con el predicado especificado de ordenación y la función hash predeterminada.  
  
 El constructor:  
  
 `hash_multiset(key_compare^ pred, hasher^ hashfn);`  
  
 Inicializa la secuencia controlada con ningún elemento con el predicado ordenación `pred`y con la función hash `hashfn`. Se usa para especificar una secuencia controlada inicial vacía, con la función de predicado y hash ordenación especificada.  
  
 El constructor:  
  
 `hash_multiset(hash_multiset<Key>% right);`  
  
 Inicializa la secuencia controlada a la secuencia [`right.begin()`, `right.end()`), con el predicado del orden predeterminado y con la función hash predeterminada. Se usa para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto hash_multiset `right`, con el predicado de ordenación predeterminado y la función hash.  
  
 El constructor:  
  
 `hash_multiset(hash_multiset<Key>^ right);`  
  
 Inicializa la secuencia controlada a la secuencia [`right->begin()`, `right->end()`), con el predicado del orden predeterminado y con la función hash predeterminada. Se usa para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto hash_multiset `right`, con el predicado de ordenación predeterminado y la función hash.  
  
 El constructor:  
  
 `template<typename InIter> hash_multiset(InIter first, InIter last);`  
  
 Inicializa la secuencia controlada a la secuencia [`first`, `last`), con el predicado del orden predeterminado y con la función hash predeterminada. Usa para hacer una copia de otra secuencia de la secuencia controlada con la función de predicado y hash del orden predeterminado.  
  
 El constructor:  
  
 `template<typename InIter> hash_multiset(InIter first, InIter last, key_compare^ pred);`  
  
 Inicializa la secuencia controlada a la secuencia [`first`, `last`), con el predicado ordenación `pred`y con la función hash predeterminada. Usa para realizar una copia de otra secuencia, con el predicado especificado de ordenación y la función hash predeterminada de la secuencia controlada.  
  
 El constructor:  
  
 `template<typename InIter> hash_multiset(InIter first, InIter last, key_compare^ pred, hasher^ hashfn);`  
  
 Inicializa la secuencia controlada a la secuencia [`first`, `last`), con el predicado ordenación `pred`y con la función hash `hashfn`. Usa para realizar una copia de otra secuencia, con la función de predicado y hash ordenación especificada de la secuencia controlada.  
  
 El constructor:  
  
 `hash_multiset(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 Inicializa la secuencia controlada con la secuencia designada por el enumerador `right`, con el predicado del orden predeterminado y con la función hash predeterminada. Usa para realizar una copia de otra secuencia descrita por un enumerador con la función de predicado y hash del orden predeterminado de la secuencia controlada.  
  
 El constructor:  
  
 `hash_multiset(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`  
  
 Inicializa la secuencia controlada con la secuencia designada por el enumerador `right`, con el predicado ordenación `pred`y con la función hash predeterminada. Usa para realizar una copia de otra secuencia descrita por un enumerador con la ordenación predeterminada y predicado hash función especificada de la secuencia controlada.  
  
 El constructor:  
  
 `hash_multiset(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred, hasher^ hashfn);`  
  
 Inicializa la secuencia controlada con la secuencia designada por el enumerador `right`, con el predicado ordenación `pred`y con la función hash `hashfn`. Usa para realizar una copia de otra secuencia descrita por un enumerador con la función de predicado y hash ordenación especificada de la secuencia controlada.  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
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
  
```Output  
size() = 0  
 a b c  
size() = 0  
 a b c  
size() = 0  
 c b a  
  
 a b c  
 a b c  
 c b a  
  
 a b c  
 a b c  
 c b a  
  
 a b c  
 a b c  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/hash_set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_multiset::generic_container (STL/CLR)](../dotnet/hash-multiset-generic-container-stl-clr.md)   
 [hash_multiset::operator= (STL/CLR)](../dotnet/hash-multiset-operator-assign-stl-clr.md)