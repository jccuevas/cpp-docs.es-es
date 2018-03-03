---
title: operador&lt; (par) (STL/CLR) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::pair::operator<
dev_langs:
- C++
helpviewer_keywords:
- operator< member [STL/CLR]
ms.assetid: e7061b29-1289-4ea9-ae69-feea8abbfb25
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3deb4737f8e82dd6fa8cd7ce99bfa67ed9f1b5fd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="operatorlt-pair-stlclr"></a>operador&lt; (par) (STL/CLR)
Par de comparación menor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<typename Value1,  
    typename Value2>  
    bool operator<(pair<Value1, Value2>% left,  
        pair<Value1, Value2>% right);  
```  
  
#### <a name="parameters"></a>Parámetros  
 izquierda  
 Par izquierdo para comparar.  
  
 right  
 Par derecho a comparar.  
  
## <a name="remarks"></a>Comentarios  
 Devuelve la función de operador `left.first <` `right.first || !(right.first <` `left.first &&` `left.second <` `right.second`. Se usa para comprobar si `left` se ordena la antes `right` cuando los dos pares no son comparado elemento por elemento.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_pair_operator_lt.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
    cliext::pair<wchar_t, int> c2(L'x', 4);   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
  
    System::Console::WriteLine("[x 3] < [x 3] is {0}",   
        c1 < c1);   
    System::Console::WriteLine("[x 3] < [x 4] is {0}",   
        c1 < c2);   
    return (0);   
    }  
  
```  
  
```Output  
[x, 3]  
[x, 4]  
[x 3] < [x 3] is False  
[x 3] < [x 4] is True  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/utilidad >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [par (STL/CLR)](../dotnet/pair-stl-clr.md)   
 [operador == (par) (STL/CLR)](../dotnet/operator-equality-pair-stl-clr.md)   
 [operador! = (par) (STL/CLR)](../dotnet/operator-inequality-pair-stl-clr.md)   
 [operador > = (par) (STL/CLR)](../dotnet/operator-greater-or-equal-pair-stl-clr.md)   
 [operador > (par) (STL/CLR)](../dotnet/operator-greater-than-pair-stl-clr.md)   
 [operator<= (pair) (STL/CLR)](../dotnet/operator-less-or-equal-pair-stl-clr.md)