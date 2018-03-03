---
title: 'Map:: rbegin (STL/CLR) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::map::rbegin
dev_langs:
- C++
helpviewer_keywords:
- rbegin member [STL/CLR]
ms.assetid: bd7165a3-561f-48d4-9791-7aaafc2cf3a5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2afe7c7a7c3cab411a236339fd2a504308c07141
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="maprbegin-stlclr"></a>map::rbegin (STL/CLR)
Designa el principio de la secuencia controlada inversa.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
reverse_iterator rbegin();  
```  
  
## <a name="remarks"></a>Comentarios  
 La función miembro devuelve un iterador inverso que designa el último elemento de la secuencia controlada o inmediatamente después del principio de una secuencia vacía. Por tanto, designa el `beginning` de la secuencia inversa. Utilícelo para obtener un iterador que designa el `current` a partir de la secuencia controlada mostrada en orden inverso, pero su estado puede cambiar si cambia la longitud de la secuencia controlada.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_map_rbegin.cpp   
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
  
// inspect first two items in reversed sequence   
    Mymap::reverse_iterator rit = c1.rbegin();   
    System::Console::WriteLine("*rbegin() = [{0} {1}]",   
        rit->first, rit->second);   
    ++rit;   
    System::Console::WriteLine("*++rbegin() = [{0} {1}]",   
        rit->first, rit->second);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
*rbegin() = [c 3]  
*++rbegin() = [b 2]  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/mapa >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [asignar (STL/CLR)](../dotnet/map-stl-clr.md)   
 [Map:: begin (STL/CLR)](../dotnet/map-begin-stl-clr.md)   
 [Map:: end (STL/CLR)](../dotnet/map-end-stl-clr.md)   
 [map::rend (STL/CLR)](../dotnet/map-rend-stl-clr.md)