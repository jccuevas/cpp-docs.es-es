---
title: push_front (STL/CLR) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::deque::push_front
dev_langs:
- C++
helpviewer_keywords:
- push_front member [STL/CLR]
ms.assetid: a452c94e-abad-4e28-af41-c73ec805ec6f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: feb464e1465834e97e4078daca1e7e39a706051a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33109994"
---
# <a name="dequepushfront-stlclr"></a>deque::push_front (STL/CLR)
Agrega un nuevo primer elemento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void push_front(value_type val);  
```  
  
## <a name="remarks"></a>Comentarios  
 La función miembro inserta un elemento con el valor `val` al principio de la secuencia controlada. Usarlo para anteponer otro elemento en el deque.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_deque_push_front.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_front(L'a');   
    c1.push_front(L'b');   
    c1.push_front(L'c');   
  
// display contents " c b a"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c b a  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/deque >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [deque:: pop_back (STL/CLR)](../dotnet/deque-pop-back-stl-clr.md)   
 [deque:: pop_front (STL/CLR)](../dotnet/deque-pop-front-stl-clr.md)   
 [deque::push_back (STL/CLR)](../dotnet/deque-push-back-stl-clr.md)