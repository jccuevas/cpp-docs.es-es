---
title: 'MULTISET:: const_iterator (STL/CLR) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::multiset::const_iterator
dev_langs:
- C++
helpviewer_keywords:
- const_iterator member [STL/CLR]
ms.assetid: 42855717-f118-4315-95b0-763f94bba888
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e8bb2c9b98ed7b17ff2e0a406e659d2d6ba74838
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33133251"
---
# <a name="multisetconstiterator-stlclr"></a>multiset::const_iterator (STL/CLR)
El tipo de un iterador constante para la secuencia controlada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef T2 const_iterator;  
```  
  
## <a name="remarks"></a>Comentarios  
 El tipo describe un objeto de tipo no especificado `T2` que puede actuar como un iterador constante bidireccional para la secuencia controlada.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_multiset_const_iterator.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    Mymultiset::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        System::Console::Write(" {0}", *cit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [MULTISET (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [multiset::iterator (STL/CLR)](../dotnet/multiset-iterator-stl-clr.md)