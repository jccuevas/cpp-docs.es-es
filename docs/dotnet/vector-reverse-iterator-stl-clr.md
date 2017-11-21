---
title: 'Vector:: reverse_iterator (STL/CLR) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::vector::reverse_iterator
dev_langs: C++
helpviewer_keywords: reverse_iterator member [STL/CLR]
ms.assetid: 0a90c5ee-a95f-4f71-a027-f1668000ccd4
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 04a4048c8ebb108efef9c4a6181f864eb2d9d708
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="vectorreverseiterator-stlclr"></a>vector::reverse_iterator (STL/CLR)
El tipo de un iterador invertido para la secuencia controlada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef T3 reverse_iterator;  
```  
  
## <a name="remarks"></a>Comentarios  
 El tipo describe un objeto de tipo no especificado `T3` que puede actuar como un iterador inverso de la secuencia controlada.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_vector_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" reversed   
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rbegin();   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" {0}", *rit);   
    System::Console::WriteLine();   
  
// alter first element and redisplay   
    rit = c1.rbegin();   
    *rit = L'x';   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" {0}", *rit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c b a  
x b a  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/vector >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [vector (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [Vector:: const_iterator (STL/CLR)](../dotnet/vector-const-iterator-stl-clr.md)   
 [Vector:: const_reverse_iterator (STL/CLR)](../dotnet/vector-const-reverse-iterator-stl-clr.md)   
 [vector::iterator (STL/CLR)](../dotnet/vector-iterator-stl-clr.md)