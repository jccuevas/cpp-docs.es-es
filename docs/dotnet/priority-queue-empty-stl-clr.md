---
title: 'priority_queue:: Empty (STL/CLR) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::priority_queue::empty
dev_langs: C++
helpviewer_keywords: empty member [STL/CLR]
ms.assetid: bb2bc4cf-395f-4c4f-b432-550b85e1865d
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 26426ddd55a6c0f8c5aeededb5a4766f7a4ce796
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="priorityqueueempty-stlclr"></a>priority_queue::empty (STL/CLR)
Comprueba si no hay ningún elemento presente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
bool empty();  
```  
  
## <a name="remarks"></a>Comentarios  
 La función miembro devuelve true para una secuencia controlada vacía. Es equivalente a [priority_queue:: Size (STL/CLR)](../dotnet/priority-queue-size-stl-clr.md)`() == 0`. Se usa para comprobar si la priority_queue está vacía.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_priority_queue_empty.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    System::Console::WriteLine("empty() = {0}", c1.empty());   
  
// clear the container and reinspect   
    c1.pop();   
    c1.pop();   
    c1.pop();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    System::Console::WriteLine("empty() = {0}", c1.empty());   
    return (0);   
    }  
  
```  
  
```Output  
 c a b  
size() = 3  
empty() = False  
size() = 0  
empty() = True  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/cola >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)   
 [priority_queue::size (STL/CLR)](../dotnet/priority-queue-size-stl-clr.md)