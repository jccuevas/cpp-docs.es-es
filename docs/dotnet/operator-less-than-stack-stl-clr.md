---
title: operador&lt; (pila) (STL/CLR) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::stack::operator<
dev_langs:
- C++
helpviewer_keywords:
- operator< member [STL/CLR]
ms.assetid: 77f8dd42-89d1-4ce1-a7ec-04c3a45dd3ee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 77ed992b33dee758b6ca7d2997135b704863c02c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33136954"
---
# <a name="operatorlt-stack-stlclr"></a>operador&lt; (pila) (STL/CLR)
Pila menor de comparación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<typename Value,  
    typename Container>  
    bool operator<(stack<Value, Container>% left,  
        stack<Value, Container>% right);  
```  
  
#### <a name="parameters"></a>Parámetros  
 izquierda  
 Contenedor izquierdo que se va a comparar.  
  
 right  
 Contenedor derecho que se va a comparar.  
  
## <a name="remarks"></a>Comentarios  
 El operador función devuelve true si, para la posición más baja `i` que `!(right[i] < left[i])` es también true que `left[i] < right[i]`. De lo contrario, devuelve `left->` [Stack:: Size (STL/CLR)](../dotnet/stack-size-stl-clr.md) `() <` `right->size()` se usa para comprobar si `left` está ordenado antes `right` cuando las dos pilas están comparado elemento por elemento.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_stack_operator_lt.cpp   
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
  
// assign to a new container   
    Mystack c2;   
    c2.push(L'a');   
    c2.push(L'b');   
    c2.push(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] < [a b c] is {0}",   
        c1 < c1);   
    System::Console::WriteLine("[a b c] < [a b d] is {0}",   
        c1 < c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] < [a b c] is False  
[a b c] < [a b d] is True  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/pila >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [pila (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [operador == (pila) (STL/CLR)](../dotnet/operator-equality-stack-stl-clr.md)   
 [operador! = (pila) (STL/CLR)](../dotnet/operator-inequality-stack-stl-clr.md)   
 [operador > = (pila) (STL/CLR)](../dotnet/operator-greater-or-equal-stack-stl-clr.md)   
 [operador > (pila) (STL/CLR)](../dotnet/operator-greater-than-stack-stl-clr.md)   
 [operator<= (stack) (STL/CLR)](../dotnet/operator-less-or-equal-stack-stl-clr.md)