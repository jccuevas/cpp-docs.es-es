---
title: 'Vector:: reserve (STL/CLR) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::vector::reserve
dev_langs: C++
helpviewer_keywords: reserve member [STL/CLR]
ms.assetid: d1d5ede9-9628-4b55-95ec-f087a57205f2
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2c8c5ac474cc2b94baedab64854fec3ca3e0a78a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="vectorreserve-stlclr"></a>vector::reserve (STL/CLR)
Garantiza una capacidad de crecimiento mínimo para el contenedor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void reserve(size_type count);  
```  
  
#### <a name="parameters"></a>Parámetros  
 count  
 Nueva capacidad mínima del contenedor.  
  
## <a name="remarks"></a>Comentarios  
 La función miembro garantiza que `capacity()` de ahora en adelante se devuelve al menos `count`. Usa para asegurarse de que el contenedor no necesita reasignar el almacenamiento de la secuencia controlada hasta que ha crecido hasta el tamaño especificado.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_vector_reserve.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1.at(i));   
    System::Console::WriteLine();   
  
// increase capacity   
    cliext::vector<wchar_t>::size_type cap = c1.capacity();   
    System::Console::WriteLine("capacity() = {0}, ok = {1}",   
        cap, c1.size() <= cap);   
    c1.reserve(cap + 5);   
    System::Console::WriteLine("capacity() = {0}, ok = {1}",   
        c1.capacity(), cap + 5 <= c1.capacity());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
capacity() = 4, ok = True  
capacity() = 9, ok = True  
```  
  
## <a name="description"></a>Descripción  
 Tenga en cuenta que las capacidades reales pueden diferir de los valores mostrados en este caso, tanto tiempo como todos los `ok` prueban no informan de true.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/vector >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [vector (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [Vector:: Capacity (STL/CLR)](../dotnet/vector-capacity-stl-clr.md)   
 [vector::resize (STL/CLR)](../dotnet/vector-resize-stl-clr.md)