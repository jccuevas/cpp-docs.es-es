---
title: 'Map:: Find (STL/CLR) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::map::find
dev_langs:
- C++
helpviewer_keywords:
- find member [STL/CLR]
ms.assetid: 779dcbee-d584-4fbd-b788-481e094ece9d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 44db80acf715cb68d426831a3b187cb2214a2ef2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="mapfind-stlclr"></a>map::find (STL/CLR)
Busca un elemento que coincide con una clave especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
iterator find(key_type key);  
```  
  
#### <a name="parameters"></a>Parámetros  
 key  
 Valor de clave que se va a buscar.  
  
## <a name="remarks"></a>Comentarios  
 Si al menos un elemento de la secuencia controlada tiene una ordenación equivalente con `key`, la función miembro devuelve un iterador que designa uno de esos elementos; de lo contrario, devuelve [Map:: end (STL/CLR)](../dotnet/map-end-stl-clr.md)`()`. Usa para buscar un elemento actualmente en la secuencia controlada que coincida con una clave especificada.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_map_find.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("find {0} = {1}",   
        L'A', c1.find(L'A') != c1.end());   
  
    Mymap::iterator it = c1.find(L'b');   
    System::Console::WriteLine("find {0} = [{1} {2}]",   
        L'b', it->first, it->second);   
  
    System::Console::WriteLine("find {0} = {1}",   
        L'C', c1.find(L'C') != c1.end());   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
find A = False  
find b = [b 2]  
find C = False  
```  
  
## <a name="description"></a>Descripción  
 Tenga en cuenta que `find` no garantiza que varios elemento que se encuentra.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/mapa >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [asignar (STL/CLR)](../dotnet/map-stl-clr.md)   
 [Map:: equal_range (STL/CLR)](../dotnet/map-equal-range-stl-clr.md)   
 [Map:: lower_bound (STL/CLR)](../dotnet/map-lower-bound-stl-clr.md)   
 [map::upper_bound (STL/CLR)](../dotnet/map-upper-bound-stl-clr.md)