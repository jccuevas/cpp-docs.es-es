---
title: 'priority_queue:: container_type (STL/CLR) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::priority_queue::container_type
dev_langs:
- C++
helpviewer_keywords:
- container_type member [STL/CLR]
ms.assetid: 97d79791-53cb-48f9-a139-69502517569f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 385ea09eb46a2253b859d7bbc46f9062b0430ec8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="priorityqueuecontainertype-stlclr"></a>priority_queue::container_type (STL/CLR)
Tipo del contenedor subyacente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef Container value_type;  
```  
  
## <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo del parámetro de plantilla `Container`.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_priority_queue_container_type.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c" using container_type   
    Mypriority_queue::container_type wc1 = c1.get_container();   
    for each (wchar_t elem in wc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c a b  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/cola >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [priority_queue::get_container (STL/CLR)](../dotnet/priority-queue-get-container-stl-clr.md)