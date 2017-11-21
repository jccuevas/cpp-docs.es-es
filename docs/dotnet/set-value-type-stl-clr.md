---
title: 'Set:: value_type (STL/CLR) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::set::value_type
dev_langs: C++
helpviewer_keywords: value_type member [STL/CLR]
ms.assetid: 9af2fe12-9a8e-4919-9619-7a2f80988951
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e26cfef4ebe1ba904cc374cf7bfed5862607e77d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="setvaluetype-stlclr"></a>set::value_type (STL/CLR)
El tipo de un elemento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
typedef generic_value value_type;  
  
```  
  
## <a name="remarks"></a>Comentarios  
 El tipo es un sinónimo de `generic_value`.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_set_value_type.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" using value_type   
    for (Myset::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in value_type object   
        Myset::value_type val = *it;   
  
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
 [Set (STL/CLR)](../dotnet/set-stl-clr.md)   
 [Set:: const_reference (STL/CLR)](../dotnet/set-const-reference-stl-clr.md)   
 [Set:: KEY_TYPE (STL/CLR)](../dotnet/set-key-type-stl-clr.md)   
 [set::reference (STL/CLR)](../dotnet/set-reference-stl-clr.md)