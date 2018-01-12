---
title: 'Map:: Size (STL/CLR) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::map::size
dev_langs: C++
helpviewer_keywords: size member [STL/CLR]
ms.assetid: e28e5ab6-9d3f-4aab-8bb4-c90520776239
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5f00a59d455067d9eb3b9ed46fe16b14c545b455
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="mapsize-stlclr"></a>map::size (STL/CLR)
Cuenta el número de elementos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
size_type size();  
```  
  
## <a name="remarks"></a>Comentarios  
 La función miembro devuelve la longitud de la secuencia controlada. Usa para determinar el número de elementos actualmente en la secuencia controlada. Si todo lo que le interesa es si la secuencia tiene tamaño distinto de cero, vea [Map:: Empty (STL/CLR)](../dotnet/map-empty-stl-clr.md)`()`.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_map_size.cpp   
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
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0} after clearing", c1.size());   
  
// add elements and clear again   
    c1.insert(Mymap::make_value(L'd', 4));   
    c1.insert(Mymap::make_value(L'e', 5));   
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
size() = 0 after clearing  
size() = 2 after adding 2  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/mapa >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [asignar (STL/CLR)](../dotnet/map-stl-clr.md)   
 [map::empty (STL/CLR)](../dotnet/map-empty-stl-clr.md)