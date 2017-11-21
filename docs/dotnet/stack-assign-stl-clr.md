---
title: Stack::assign (STL/CLR) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::stack::assign
dev_langs: C++
helpviewer_keywords: assign member [STL/CLR]
ms.assetid: 18cc35ad-23cf-4a5a-adae-d967dc5d6980
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 11214550141cc32c589ef090c48775390bc26627
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="stackassign-stlclr"></a>stack::assign (STL/CLR)
Reemplaza todos los elementos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void assign(stack<Value, Container>% right);  
```  
  
#### <a name="parameters"></a>Parámetros  
 right  
 Adaptador de contenedor para insertar.  
  
## <a name="remarks"></a>Comentarios  
 La función miembro asigna `right.get_container()` al contenedor subyacente. Usa para cambiar todo el contenido de la pila.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_stack_assign.cpp   
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
  
// assign a repetition of values   
    Mystack c2;   
    c2.assign(c1);   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/pila >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [pila (STL/CLR)](../dotnet/stack-stl-clr.md)   
 [stack::operator= (STL/CLR)](../dotnet/stack-operator-assign-stl-clr.md)