---
title: 'hash_multiset:: upper_bound (STL/CLR) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_multiset::upper_bound
dev_langs:
- C++
helpviewer_keywords:
- upper_bound member [STL/CLR]
ms.assetid: d5be0d79-ae60-42bb-8a53-051bc374407d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f6555a0ca3b3712d48def412c1e2e92d3dde95af
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33127271"
---
# <a name="hashmultisetupperbound-stlclr"></a>hash_multiset::upper_bound (STL/CLR)
Busca el final del intervalo que coincide con una clave especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
iterator upper_bound(key_type key);  
```  
  
#### <a name="parameters"></a>Parámetros  
 key  
 Valor de clave que se va a buscar.  
  
## <a name="remarks"></a>Comentarios  
 La función miembro determina el último elemento `X` en la secuencia controlada que aplica un algoritmo hash al mismo depósito como `key` y tiene una ordenación equivalente a `key`. Si no existe ese elemento, o si `X` es el último elemento de la secuencia controlada, devuelve [hash_multiset:: end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md)`()`; en caso contrario, devuelve un iterador que designa el primer elemento más allá de `X`. Usa para buscar el final de una secuencia de elementos actualmente en la secuencia controlada que coinciden con una clave especificada.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_hash_multiset_upper_bound.cpp   
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
  
    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",   
        c1.upper_bound(L'x') == c1.end());   
  
    System::Console::WriteLine("*upper_bound(L'a') = {0}",   
        *c1.upper_bound(L'a'));   
    System::Console::WriteLine("*upper_bound(L'b') = {0}",   
        *c1.upper_bound(L'b'));   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
upper_bound(L'x')==end() = True  
*upper_bound(L'a') = b  
*upper_bound(L'b') = c  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/hash_set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_multiset:: Count (STL/CLR)](../dotnet/hash-multiset-count-stl-clr.md)   
 [hash_multiset:: equal_range (STL/CLR)](../dotnet/hash-multiset-equal-range-stl-clr.md)   
 [hash_multiset:: Find (STL/CLR)](../dotnet/hash-multiset-find-stl-clr.md)   
 [hash_multiset::lower_bound (STL/CLR)](../dotnet/hash-multiset-lower-bound-stl-clr.md)