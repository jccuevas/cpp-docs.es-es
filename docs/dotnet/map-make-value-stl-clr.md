---
title: Map::make_value (STL/CLR) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::map::make_value
dev_langs: C++
helpviewer_keywords: make_value member [STL/CLR]
ms.assetid: a0bc4081-b8b7-450e-b041-a49ac42b279f
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: de81b04cd0e63fb01b33f255dd532e70c101f868
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="mapmakevalue-stlclr"></a>map::make_value (STL/CLR)
Construye un objeto de valor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
static value_type make_value(key_type key, mapped_type mapped);  
```  
  
#### <a name="parameters"></a>Parámetros  
 key  
 Valor de clave a utilizar.  
  
 asignado  
 Valor asignado a buscar.  
  
## <a name="remarks"></a>Comentarios  
 La función miembro devuelve un `value_type` objeto cuya clave es `key` y cuyo valor asignado es `mapped`. Usarlo para crear un objeto adecuado para su uso con muchas otras funciones de miembro.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_map_make_value.cpp   
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
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/mapa >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [asignar (STL/CLR)](../dotnet/map-stl-clr.md)   
 [Map:: KEY_TYPE (STL/CLR)](../dotnet/map-key-type-stl-clr.md)   
 [Map:: mapped_type (STL/CLR)](../dotnet/map-mapped-type-stl-clr.md)   
 [map::value_type (STL/CLR)](../dotnet/map-value-type-stl-clr.md)