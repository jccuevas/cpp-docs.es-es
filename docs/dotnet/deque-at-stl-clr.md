---
title: 'deque:: AT (STL/CLR) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::deque::at
dev_langs:
- C++
helpviewer_keywords:
- at member [STL/CLR]
ms.assetid: 9af83d8a-c519-4b2a-a25f-d3dc8bbb87fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8388f6428d31cce2993e7c90db66f430564d347e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="dequeat-stlclr"></a>deque::at (STL/CLR)
Obtiene acceso a un elemento en una posición especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
reference at(size_type pos);  
```  
  
#### <a name="parameters"></a>Parámetros  
 posición  
 Posición del elemento al que se accederá.  
  
## <a name="remarks"></a>Comentarios  
 La función miembro devuelve una referencia al elemento de la secuencia controlada en la posición `pos`. Se usa para leer o escribir un elemento cuya posición conoce.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_deque_at.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" using at   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1.at(i));   
    System::Console::WriteLine();   
  
// change an entry and redisplay   
    c1.at(1) = L'x';   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1[i]);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a x c  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/deque >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [deque::operator(STL/CLR)](../dotnet/deque-operator-stl-clr.md)