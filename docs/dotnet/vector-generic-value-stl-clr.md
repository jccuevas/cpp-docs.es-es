---
title: Vector::generic_value (STL/CLR) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::vector::generic_value
dev_langs:
- C++
helpviewer_keywords:
- generic_value member [STL/CLR]
ms.assetid: 01fdc5c5-27d3-4dc2-b242-cae2fd04a60d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ef96bf732246e2ae11840468bb52586d7954cf01
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="vectorgenericvalue-stlclr"></a>vector::generic_value (STL/CLR)
El tipo de un elemento para su uso con la interfaz genérica para el contenedor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef GValue generic_value;  
```  
  
## <a name="remarks"></a>Comentarios  
 El tipo describe un objeto de tipo `GValue` que describe el valor del elemento almacenado para su uso con la interfaz genérica para esta clase de contenedor de plantilla.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_vector_generic_value.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    cliext::vector<wchar_t>::generic_iterator gcit = gc1->begin();   
    cliext::vector<wchar_t>::generic_value gcval = *gcit;   
    *++gcit = gcval;   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a a c  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/vector >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [vector (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [Vector::generic_container (STL/CLR)](../dotnet/vector-generic-container-stl-clr.md)   
 [Vector::generic_iterator (STL/CLR)](../dotnet/vector-generic-iterator-stl-clr.md)   
 [vector::generic_reverse_iterator (STL/CLR)](../dotnet/vector-generic-reverse-iterator-stl-clr.md)