---
title: 'hash_multiset:: Erase (STL/CLR) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_multiset::erase
dev_langs:
- C++
helpviewer_keywords:
- erase member [STL/CLR]
ms.assetid: bddd329d-aece-4b93-8355-005351c3aa45
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4652c4e09dbcb646888d2e4973eb982357015e7c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="hashmultiseterase-stlclr"></a>hash_multiset::erase (STL/CLR)
Quita los elementos de las posiciones especificadas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
bool erase(key_type key)  
```  
  
#### <a name="parameters"></a>Parámetros  
 first  
 Comienzo del intervalo que se va a borrar.  
  
 key  
 Valor de clave para borrar.  
  
 last  
 Final del intervalo que se va a borrar.  
  
 donde  
 Elemento que se va a borrar.  
  
## <a name="remarks"></a>Comentarios  
 La primera función miembro quita el elemento de la secuencia controlada señalada por `where`y devuelve un iterador que designa el primer elemento que permanece más allá del elemento eliminado, o [hash_multiset:: end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md) `()` si no existe ese elemento. Usa para quitar un único elemento.  
  
 La segunda función miembro quita los elementos de la secuencia controlada en el intervalo [`first`, `last`) y devuelve un iterador que designa el primer elemento que permanece más allá de los elementos quitados, o `end()` si ningún elemento existe... Usa para quitar cero o más elementos contiguos.  
  
 La tercera función miembro quita cualquier elemento de la secuencia controlada cuyo criterio de ordenación es equivalente a `key`y devuelve un recuento del número de elementos quitados. Se usa para quitar y recuento de todos los elementos que coinciden con una clave especificada.  
  
 La eliminación de cada elemento lleva tiempo proporcional al logaritmo del número de elementos de la secuencia controlada.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_hash_multiset_erase.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase an element and reinspect   
    System::Console::WriteLine("erase(begin()) = {0}",   
        *c1.erase(c1.begin()));   
  
// add elements and display " b c d e"   
    c1.insert(L'd');   
    c1.insert(L'e');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase all but end   
    Myhash_multiset::iterator it = c1.end();   
    System::Console::WriteLine("erase(begin(), end()-1) = {0}",   
        *c1.erase(c1.begin(), --it));   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
erase(begin()) = b  
 b c d e  
erase(begin(), end()-1) = e  
size() = 1  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/hash_set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_multiset::clear (STL/CLR)](../dotnet/hash-multiset-clear-stl-clr.md)