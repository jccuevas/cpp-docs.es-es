---
title: 'Queue:: Queue (STL/CLR) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::queue::queue
dev_langs:
- C++
helpviewer_keywords:
- queue member [STL/CLR]
ms.assetid: 6106c07f-d5eb-4f0b-82df-ee4e2e751047
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d6c4b24ad40bf19b7a20aafcfa2d02fb6490fed1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="queuequeue-stlclr"></a>queue::queue (STL/CLR)
Construye un objeto de adaptador de contenedor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
queue();  
queue(queue<Value, Container>% right);  
queue(queue<Value, Container>^ right);  
explicit queue(container_type% wrapped);  
```  
  
#### <a name="parameters"></a>Parámetros  
 right  
 Objeto que se va a copiar.  
  
 ajustado  
 Contenedor ajustada que se va a usar.  
  
## <a name="remarks"></a>Comentarios  
 El constructor:  
  
 `queue();`  
  
 crea un contenedor vacío ajustado. Se usa para especificar una secuencia controlada inicial vacía.  
  
 El constructor:  
  
 `queue(queue<Value, Container>% right);`  
  
 crea un contenedor ajustado que es una copia de `right.get_container()`. Se usa para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto de cola `right`.  
  
 El constructor:  
  
 `queue(queue<Value, Container>^ right);`  
  
 crea un contenedor ajustado que es una copia de `right->get_container()`. Se usa para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto de cola `*right`.  
  
 El constructor:  
  
 `explicit queue(container_type wrapped);`  
  
 usa el contenedor existente `wrapped` como el contenedor ajustado. Se utiliza para crear una cola desde un contenedor existente.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_queue_construct.cpp   
// compile with: /clr   
#include <cliext/queue>   
#include <cliext/list>   
  
typedef cliext::queue<wchar_t> Myqueue;   
typedef cliext::list<wchar_t> Mylist;   
typedef cliext::queue<wchar_t, Mylist> Myqueue_list;   
int main()   
    {   
// construct an empty container   
    Myqueue c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct from an underlying container   
    Mylist v2(5, L'x');   
    Myqueue_list c2(v2);       
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Myqueue_list c3(c2);   
    for each (wchar_t elem in c3.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container through handle   
    Myqueue_list c4(%c2);   
    for each (wchar_t elem in c4.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 x x x x x  
 x x x x x  
 x x x x x  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/cola >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [cola (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [Queue::assign (STL/CLR)](../dotnet/queue-assign-stl-clr.md)   
 [Queue::generic_container (STL/CLR)](../dotnet/queue-generic-container-stl-clr.md)   
 [queue::operator= (STL/CLR)](../dotnet/queue-operator-assign-stl-clr.md)