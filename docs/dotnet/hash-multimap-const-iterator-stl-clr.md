---
title: 'hash_multimap:: const_iterator (STL/CLR) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::hash_multimap::const_iterator
dev_langs: C++
helpviewer_keywords: const_iterator member [STL/CLR]
ms.assetid: 3d54185c-7d30-41e6-8837-92e62448bc8e
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 613b0a77a2455bb5af246635302c040cf6b3c813
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="hashmultimapconstiterator-stlclr"></a>hash_multimap::const_iterator (STL/CLR)
El tipo de un iterador constante para la secuencia controlada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef T2 const_iterator;  
```  
  
## <a name="remarks"></a>Comentarios  
 El tipo describe un objeto de tipo no especificado `T2` que puede actuar como un iterador constante bidireccional para la secuencia controlada.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_hash_multimap_const_iterator.cpp   
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
    Myhash_multimap::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        System::Console::Write(" [{0} {1}]", cit->first, cit->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/hash_map >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [hash_multimap (STL/CLR)](../dotnet/hash-multimap-stl-clr.md)   
 [hash_multimap::iterator (STL/CLR)](../dotnet/hash-multimap-iterator-stl-clr.md)