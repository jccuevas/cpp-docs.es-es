---
title: 'hash_map:: KEY_TYPE (STL/CLR) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_map::key_type
dev_langs:
- C++
helpviewer_keywords:
- key_type member [STL/CLR]
ms.assetid: 1e7d0f40-03e0-4413-b652-1d9fe14f0f12
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 02f549a9d2fcf255d2e4aeaf91f7308d2e2cb382
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33110098"
---
# <a name="hashmapkeytype-stlclr"></a>hash_map::key_type (STL/CLR)
El tipo de una clave de ordenación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef Key key_type;  
```  
  
## <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla `Key`.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_hash_map_key_type.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]" using key_type   
    for (Myhash_map::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in key_type object   
        Myhash_map::key_type val = it->first;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/hash_map >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_map:: key_compare (STL/CLR)](../dotnet/hash-map-key-compare-stl-clr.md)   
 [hash_map:: mapped_type (STL/CLR)](../dotnet/hash-map-mapped-type-stl-clr.md)   
 [hash_map::value_type (STL/CLR)](../dotnet/hash-map-value-type-stl-clr.md)