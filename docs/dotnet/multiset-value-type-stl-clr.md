---
title: 'MULTISET:: value_type (STL/CLR) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::multiset::value_type
dev_langs:
- C++
helpviewer_keywords:
- value_type member [STL/CLR]
ms.assetid: 6a88ee7a-27a1-4fbb-a56c-9c8d7abc4471
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: db7850cf6984d645e5f60045d236222c82bf632c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="multisetvaluetype-stlclr"></a>multiset::value_type (STL/CLR)
El tipo de un elemento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef generic_value value_type;  
```  
  
## <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo de `generic_value`.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_multiset_value_type.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" using value_type   
    for (Mymultiset::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in value_type object   
        Mymultiset::value_type val = *it;   
  
        System::Console::Write(" {0}", val);   
        }   
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
 [MULTISET:: const_reference (STL/CLR)](../dotnet/multiset-const-reference-stl-clr.md)   
 [MULTISET:: KEY_TYPE (STL/CLR)](../dotnet/multiset-key-type-stl-clr.md)   
 [multiset::reference (STL/CLR)](../dotnet/multiset-reference-stl-clr.md)