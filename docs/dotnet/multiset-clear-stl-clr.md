---
title: 'MULTISET:: Clear (STL/CLR) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::multiset::clear
dev_langs:
- C++
helpviewer_keywords:
- clear member [STL/CLR]
ms.assetid: 63c21716-fa08-47b9-b457-0b76052c5079
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f12141a08ffdeeb3ced26d4313a8cfb245d2f3a9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="multisetclear-stlclr"></a>multiset::clear (STL/CLR)
Quita todos los elementos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void clear();  
```  
  
## <a name="remarks"></a>Comentarios  
 La función miembro llama eficazmente a [MULTISET:: Erase (STL/CLR)](../dotnet/multiset-erase-stl-clr.md) `(` [MULTISET:: begin (STL/CLR)](../dotnet/multiset-begin-stl-clr.md) `(),` [MULTISET:: end (STL/CLR)](../dotnet/multiset-end-stl-clr.md) `())`. Utilizarlo para asegurarse de que la secuencia controlada está vacía.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_multiset_clear.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// add elements and clear again   
    c1.insert(L'a');   
    c1.insert(L'b');   
  
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
size() = 0  
 a b  
size() = 0  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [MULTISET (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [multiset::erase (STL/CLR)](../dotnet/multiset-erase-stl-clr.md)