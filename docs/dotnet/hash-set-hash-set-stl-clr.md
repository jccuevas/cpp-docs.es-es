---
title: 'hash_set:: hash_set (STL/CLR) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::hash_set::hash_set
dev_langs:
- C++
helpviewer_keywords:
- hash_set member [STL/CLR]
ms.assetid: 006414ed-db5a-4c08-ac81-4a8ae57d0aad
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a01d8dcfda1bbb7f05db9fde7b16aa5094fba2bc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="hashsethashset-stlclr"></a>hash_set::hash_set (STL/CLR)
Construye un objeto contenedor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
hash_set();  
explicit hash_set(key_compare^ pred);  
hash_set(key_compare^ pred, hasher^ hashfn);  
hash_set(hash_set<Key>% right);  
hash_set(hash_set<Key>^ right);  
template<typename InIter>  
    hash_sethash_set(InIter first, InIter last);  
template<typename InIter>  
    hash_set(InIter first, InIter last,  
        key_compare^ pred);  
template<typename InIter>  
    hash_set(InIter first, InIter last,  
        key_compare^ pred, hasher^ hashfn);  
hash_set(System::Collections::Generic::IEnumerable<GValue>^ right);  
hash_set(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred);  
hash_set(System::Collections::Generic::IEnumerable<GValue>^ right,  
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
  
 `hash_set();`  
  
 Inicializa la secuencia controlada con ningún elemento con el predicado del orden predeterminado `key_compare()`y con la función hash predeterminada. Se usa para especificar una secuencia controlada inicial vacía, con la función de predicado y hash del orden predeterminado.  
  
 El constructor:  
  
 `explicit hash_set(key_compare^ pred);`  
  
 Inicializa la secuencia controlada con ningún elemento con el predicado ordenación `pred`y con la función hash predeterminada. Se usa para especificar una secuencia controlada inicial vacía, con el predicado especificado de ordenación y la función hash predeterminada.  
  
 El constructor:  
  
 `hash_set(key_compare^ pred, hasher^ hashfn);`  
  
 Inicializa la secuencia controlada con ningún elemento con el predicado ordenación `pred`y con la función hash `hashfn`. Se usa para especificar una secuencia controlada inicial vacía, con la función de predicado y hash ordenación especificada.  
  
 El constructor:  
  
 `hash_set(hash_set<Key>% right);`  
  
 Inicializa la secuencia controlada a la secuencia [`right.begin()`, `right.end()`), con el predicado del orden predeterminado y con la función hash predeterminada. Se usa para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto hash_set `right`, con el predicado de ordenación predeterminado y la función hash.  
  
 El constructor:  
  
 `hash_set(hash_set<Key>^ right);`  
  
 Inicializa la secuencia controlada a la secuencia [`right->begin()`, `right->end()`), con el predicado del orden predeterminado y con la función hash predeterminada. Se usa para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto hash_set `right`, con el predicado de ordenación predeterminado y la función hash.  
  
 El constructor:  
  
 `template<typename InIter> hash_set(InIter first, InIter last);`  
  
 Inicializa la secuencia controlada a la secuencia [`first`, `last`), con el predicado del orden predeterminado y con la función hash predeterminada. Usa para hacer una copia de otra secuencia de la secuencia controlada con la función de predicado y hash del orden predeterminado.  
  
 El constructor:  
  
 `template<typename InIter> hash_set(InIter first, InIter last, key_compare^ pred);`  
  
 Inicializa la secuencia controlada a la secuencia [`first`, `last`), con el predicado ordenación `pred`y con la función hash predeterminada. Usa para realizar una copia de otra secuencia, con el predicado especificado de ordenación y la función hash predeterminada de la secuencia controlada.  
  
 El constructor:  
  
 `template<typename InIter> hash_set(InIter first, InIter last, key_compare^ pred, hasher^ hashfn);`  
  
 Inicializa la secuencia controlada a la secuencia [`first`, `last`), con el predicado ordenación `pred`y con la función hash `hashfn`. Usa para realizar una copia de otra secuencia, con la función de predicado y hash ordenación especificada de la secuencia controlada.  
  
 El constructor:  
  
 `hash_set(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 Inicializa la secuencia controlada con la secuencia designada por el enumerador `right`, con el predicado del orden predeterminado y con la función hash predeterminada. Usa para realizar una copia de otra secuencia descrita por un enumerador con la función de predicado y hash del orden predeterminado de la secuencia controlada.  
  
 El constructor:  
  
 `hash_set(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`  
  
 Inicializa la secuencia controlada con la secuencia designada por el enumerador `right`, con el predicado ordenación `pred`y con la función hash predeterminada. Usa para realizar una copia de otra secuencia descrita por un enumerador con la ordenación predeterminada y predicado hash función especificada de la secuencia controlada.  
  
 El constructor:  
  
 `hash_set(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred, hasher^ hashfn);`  
  
 Inicializa la secuencia controlada con la secuencia designada por el enumerador `right`, con el predicado ordenación `pred`y con la función hash `hashfn`. Usa para realizar una copia de otra secuencia descrita por un enumerador con la función de predicado y hash ordenación especificada de la secuencia controlada.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_hash_set_construct.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
int myfun(wchar_t key)   
    { // hash a key   
    return (key ^ 0xdeadbeef);   
    }   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
// construct an empty container   
    Myhash_set c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Myhash_set c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule and hash function   
    Myhash_set c2h(cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_set::hasher(&myfun));   
    System::Console::WriteLine("size() = {0}", c2h.size());   
  
    c2h.insert(c1.begin(), c1.end());   
    for each (wchar_t elem in c2h)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Myhash_set c3(c1.begin(), c1.end());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Myhash_set c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule and hash function   
    Myhash_set c4h(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_set::hasher(&myfun));   
    for each (wchar_t elem in c4h)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Myhash_set c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Myhash_set c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,   
            cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c6)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule and hash function   
    Myhash_set c6h(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,   
            cliext::greater_equal<wchar_t>(),   
                gcnew Myhash_set::hasher(&myfun));   
    for each (wchar_t elem in c6h)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct from a generic container   
    Myhash_set c7(c4);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Myhash_set c8(%c3);   
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
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [hash_set::generic_container (STL/CLR)](../dotnet/hash-set-generic-container-stl-clr.md)   
 [hash_set::operator= (STL/CLR)](../dotnet/hash-set-operator-assign-stl-clr.md)