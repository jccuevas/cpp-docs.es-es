---
title: 'List:: pop_front (STL/CLR) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::list::pop_front
dev_langs:
- C++
helpviewer_keywords:
- pop_front member [STL/CLR]
ms.assetid: 6a0bad42-6796-41d9-a3e9-1488b3882574
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 68ceb6be19093fc99ed666e6c6e7f2a1c0cec0b2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="listpopfront-stlclr"></a>list::pop_front (STL/CLR)
Quita el primer elemento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void pop_front();  
```  
  
## <a name="remarks"></a>Comentarios  
 La función miembro quita el primer elemento de la secuencia controlada, que debe ser no está vacío. Usa para acortar la lista por un elemento al principio.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_list_pop_front.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// pop an element and redisplay   
    c1.pop_front();   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
b c  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/list >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [lista (STL/CLR)](../dotnet/list-stl-clr.md)   
 [List:: pop_back (STL/CLR)](../dotnet/list-pop-back-stl-clr.md)   
 [List:: push_back (STL/CLR)](../dotnet/list-push-back-stl-clr.md)   
 [list::push_front (STL/CLR)](../dotnet/list-push-front-stl-clr.md)