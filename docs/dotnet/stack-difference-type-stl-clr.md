---
title: Stack::difference_type (STL/CLR) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::stack::difference_type
dev_langs: C++
helpviewer_keywords: difference_type member [STL/CLR]
ms.assetid: 953a0d2a-873c-41e7-b792-15cf18e7a5b4
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 00c2a982703577f5db9a6060efaad2e20dae3f16
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="stackdifferencetype-stlclr"></a>stack::difference_type (STL/CLR)
Los tipos de una distancia con signo entre dos elementos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef int difference_type;  
```  
  
## <a name="remarks"></a>Comentarios  
 El tipo describe un recuento de elemento posiblemente negativo.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_stack_difference_type.cpp   
// compile with: /clr   
#include <cliext/stack>   
  
typedef cliext::stack<wchar_t> Mystack;   
int main()   
    {   
    Mystack c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute negative difference   
    Mystack::difference_type diff = c1.size();   
    c1.push(L'd');   
    c1.push(L'e');   
    diff -= c1.size();   
    System::Console::WriteLine("pushing 2 = {0}", diff);   
  
// compute positive difference   
    diff = c1.size();   
    c1.pop();   
    c1.pop();   
    c1.pop();   
    diff -= c1.size();   
    System::Console::WriteLine("popping 3 = {0}", diff);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
pushing 2 = -2  
popping 3 = 3  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/pila >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [pila (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [stack::size_type (STL/CLR)](../dotnet/stack-size-type-stl-clr.md)