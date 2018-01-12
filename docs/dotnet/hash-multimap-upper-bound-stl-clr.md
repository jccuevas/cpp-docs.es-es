---
title: 'hash_multimap:: upper_bound (STL/CLR) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::hash_multimap::upper_bound
dev_langs: C++
helpviewer_keywords: upper_bound member [STL/CLR]
ms.assetid: 4fa58df6-63ec-411d-bcf9-301d3c88569a
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8da5c64a24f9d31c254831e87b844feec724f254
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="hashmultimapupperbound-stlclr"></a>hash_multimap::upper_bound (STL/CLR)
Busca el final del intervalo que coincide con una clave especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
iterator upper_bound(key_type key);  
```  
  
#### <a name="parameters"></a>Parámetros  
 key  
 Valor de clave que se va a buscar.  
  
## <a name="remarks"></a>Comentarios  
 La función miembro determina el último elemento `X` en la secuencia controlada que aplica un algoritmo hash al mismo depósito como `key` y tiene una ordenación equivalente a `key`. Si no existe ese elemento, o si `X` es el último elemento de la secuencia controlada, devuelve [hash_multimap:: end (STL/CLR)](../dotnet/hash-multimap-end-stl-clr.md)`()`; en caso contrario, devuelve un iterador que designa el primer elemento más allá de `X`. Usa para buscar el final de una secuencia de elementos actualmente en la secuencia controlada que coinciden con una clave especificada.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_hash_multimap_upper_bound.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_multimap<wchar_t, int> Myhash_multimap;   
int main()   
    {   
    Myhash_multimap c1;   
    c1.insert(Myhash_multimap::make_value(L'a', 1));   
    c1.insert(Myhash_multimap::make_value(L'b', 2));   
    c1.insert(Myhash_multimap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_multimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",   
        c1.upper_bound(L'x') == c1.end());   
  
    Myhash_multimap::iterator it = c1.upper_bound(L'a');   
    System::Console::WriteLine("*upper_bound(L'a') = [{0} {1}]",   
        it->first, it->second);   
    it = c1.upper_bound(L'b');   
    System::Console::WriteLine("*upper_bound(L'b') = [{0} {1}]",   
        it->first, it->second);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
upper_bound(L'x')==end() = True  
*upper_bound(L'a') = [b 2]  
*upper_bound(L'b') = [c 3]  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/hash_map >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [hash_multimap (STL/CLR)](../dotnet/hash-multimap-stl-clr.md)   
 [hash_multimap:: Count (STL/CLR)](../dotnet/hash-multimap-count-stl-clr.md)   
 [hash_multimap:: equal_range (STL/CLR)](../dotnet/hash-multimap-equal-range-stl-clr.md)   
 [hash_multimap:: Find (STL/CLR)](../dotnet/hash-multimap-find-stl-clr.md)   
 [hash_multimap::lower_bound (STL/CLR)](../dotnet/hash-multimap-lower-bound-stl-clr.md)