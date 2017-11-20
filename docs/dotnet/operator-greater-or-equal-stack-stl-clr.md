---
title: operador&gt;= (pila) (STL/CLR) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::stack::operator>=
dev_langs: C++
helpviewer_keywords: operator>= member [STL/CLR]
ms.assetid: d0c757fa-9d40-40c7-89f7-baf30b22d899
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8a9ce2bba389546967073dd2f3de80ad66616756
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="operatorgt-stack-stlclr"></a>operador&gt;= (pila) (STL/CLR)
Comparación igual o superior de la pila.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<typename Value,  
    typename Container>  
    bool operator>=(stack<Value, Container>% left,  
        stack<Value, Container>% right);  
```  
  
#### <a name="parameters"></a>Parámetros  
 izquierda  
 Contenedor izquierdo que se va a comparar.  
  
 derecha  
 Contenedor derecho que se va a comparar.  
  
## <a name="remarks"></a>Comentarios  
 Devuelve la función de operador `!(left < right)`. Se usa para comprobar si `left` no está ordenado antes `right` cuando las dos pilas están comparado elemento por elemento.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_stack_operator_ge.cpp   
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
  
    System::Console::WriteLine("[a b c] >= [a b c] is {0}",   
        c1 >= c1);   
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",   
        c1 >= c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] >= [a b c] is True  
[a b c] >= [a b d] is False  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/pila >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [pila (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [operador == (pila) (STL/CLR)](../dotnet/operator-equality-stack-stl-clr.md)   
 [operador! = (pila) (STL/CLR)](../dotnet/operator-inequality-stack-stl-clr.md)   
 [operador\< (pila) (STL/CLR)](../dotnet/operator-less-than-stack-stl-clr.md)   
 [operador > (pila) (STL/CLR)](../dotnet/operator-greater-than-stack-stl-clr.md)   
 [operator<= (stack) (STL/CLR)](../dotnet/operator-less-or-equal-stack-stl-clr.md)