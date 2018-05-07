---
title: 'Stack:: POP (STL/CLR) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::stack::pop
dev_langs:
- C++
helpviewer_keywords:
- pop member [STL/CLR]
ms.assetid: b7565385-9e6b-432d-8c71-c62c9c6ad90d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3a5d556768b0b3699dbc1ff226a627b9d5061303
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="stackpop-stlclr"></a>stack::pop (STL/CLR)
Quita el último elemento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void pop();  
```  
  
## <a name="remarks"></a>Comentarios  
 La función miembro quita el último elemento de la secuencia controlada, que debe ser no está vacío. Se usar para acortar la pila por un elemento en la parte posterior.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_stack_pop.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// pop an element and redisplay   
    c1.pop();   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/pila >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [pila (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [stack::push (STL/CLR)](../dotnet/stack-push-stl-clr.md)