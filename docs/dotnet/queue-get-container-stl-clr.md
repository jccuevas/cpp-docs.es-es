---
title: Queue::get_container (STL/CLR) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::queue::get_container
dev_langs:
- C++
helpviewer_keywords:
- get_container member [STL/CLR]
ms.assetid: d87e7433-a352-4bea-8041-1ffc03287436
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 26c23bead59207aca50eeef5c2891a619952a15b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="queuegetcontainer-stlclr"></a>queue::get_container (STL/CLR)
Se tiene acceso del contenedor subyacente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
container_type^ get_container();  
```  
  
## <a name="remarks"></a>Comentarios  
 La función miembro devuelve el contenedor subyacente. Usa para omitir las restricciones impuestas por el contenedor del contenedor.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_queue_get_container.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/cola >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [cola (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [queue::container_type (STL/CLR)](../dotnet/queue-container-type-stl-clr.md)