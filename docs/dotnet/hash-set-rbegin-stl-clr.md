---
title: 'hash_set:: rbegin (STL/CLR) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- cliext::hash_set::rbegin
dev_langs:
- C++
helpviewer_keywords:
- rbegin member [STL/CLR]
ms.assetid: 1f2ff4ed-8557-40cf-8e61-816563acc43e
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 33caee5f46436f7f2176d237c10744c66f4113b3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="hashsetrbegin-stlclr"></a>hash_set::rbegin (STL/CLR)
Designa el principio de la secuencia controlada inversa.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
reverse_iterator rbegin();  
```  
  
## <a name="remarks"></a>Comentarios  
 La función miembro devuelve un iterador inverso que designa el último elemento de la secuencia controlada o inmediatamente después del principio de una secuencia vacía. Por tanto, designa el `beginning` de la secuencia inversa. Utilícelo para obtener un iterador que designa el `current` a partir de la secuencia controlada mostrada en orden inverso, pero su estado puede cambiar si cambia la longitud de la secuencia controlada.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_hash_set_rbegin.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items in reversed sequence   
    Myhash_set::reverse_iterator rit = c1.rbegin();   
    System::Console::WriteLine("*rbegin() = {0}", *rit);   
    System::Console::WriteLine("*++rbegin() = {0}", *++rit);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*rbegin() = c  
*++rbegin() = b  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/hash_set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [hash_set:: begin (STL/CLR)](../dotnet/hash-set-begin-stl-clr.md)   
 [hash_set:: end (STL/CLR)](../dotnet/hash-set-end-stl-clr.md)   
 [hash_set::rend (STL/CLR)](../dotnet/hash-set-rend-stl-clr.md)