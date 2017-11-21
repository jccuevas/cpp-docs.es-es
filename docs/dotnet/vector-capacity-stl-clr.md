---
title: 'Vector:: Capacity (STL/CLR) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::vector::capacity
dev_langs: C++
helpviewer_keywords: capacity member [STL/CLR]
ms.assetid: f82d8da9-8b4d-4288-8d18-8e9ca5911d87
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 97693360d03f0c861f1c2f1b956fcbd136d7c6f6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="vectorcapacity-stlclr"></a>vector::capacity (STL/CLR)
Informa del tamaño de almacenamiento asignado para el contenedor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
size_type capacity();  
```  
  
## <a name="remarks"></a>Comentarios  
 La función miembro devuelve el almacenamiento asignado actualmente para contener la secuencia controlada, un valor de al menos tan grande como [vector:: Size (STL/CLR)](../dotnet/vector-size-stl-clr.md)`()`. Usa para determinar el contenedor de cuánto puede crecer antes de que debe reasignar el almacenamiento de la secuencia controlada.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_vector_capacity.cpp   
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
 [vector::reserve (STL/CLR)](../dotnet/vector-reserve-stl-clr.md)