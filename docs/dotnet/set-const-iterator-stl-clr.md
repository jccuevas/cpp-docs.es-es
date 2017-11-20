---
title: 'Set:: const_iterator (STL/CLR) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::set::const_iterator
dev_langs: C++
helpviewer_keywords: const_iterator member [STL/CLR]
ms.assetid: de234ad4-d420-4da8-a13a-1aec8c337d8b
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: dbca736fb7519cf52238135944d02a1efe603734
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="setconstiterator-stlclr"></a>set::const_iterator (STL/CLR)
El tipo de un iterador constante para la secuencia controlada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef T2 const_iterator;  
```  
  
## <a name="remarks"></a>Comentarios  
 El tipo describe un objeto de tipo no especificado `T2` que puede actuar como un iterador constante bidireccional para la secuencia controlada.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_set_const_iterator.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    Myset::const_iterator cit = c1.begin();   
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
 [Set (STL/CLR)](../dotnet/set-stl-clr.md)   
 [set::iterator (STL/CLR)](../dotnet/set-iterator-stl-clr.md)