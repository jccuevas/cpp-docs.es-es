---
title: 'Set:: lower_bound (STL/CLR) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::set::lower_bound
dev_langs:
- C++
helpviewer_keywords:
- lower_bound member [STL/CLR]
ms.assetid: d4da5b8b-ddf2-4d36-8092-f1be81b42348
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3e5c455291f6b109ff117503739d6022aab87fd7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33163385"
---
# <a name="setlowerbound-stlclr"></a>set::lower_bound (STL/CLR)
Busca el comienzo del intervalo que coincide con una clave especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
iterator lower_bound(key_type key);  
```  
  
#### <a name="parameters"></a>Parámetros  
 key  
 Valor de clave que se va a buscar.  
  
## <a name="remarks"></a>Comentarios  
 La función miembro determina el primer elemento `X` en la secuencia controlada que tiene una ordenación equivalente a `key`. Si no existe ese elemento, devuelve [Set:: end (STL/CLR)](../dotnet/set-end-stl-clr.md)`()`; en caso contrario, devuelve un iterador que designa `X`. Usa para buscar el principio de una secuencia de elementos actualmente en la secuencia controlada que coinciden con una clave especificada.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_set_lower_bound.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",   
        c1.lower_bound(L'x') == c1.end());   
  
    System::Console::WriteLine("*lower_bound(L'a') = {0}",   
        *c1.lower_bound(L'a'));   
    System::Console::WriteLine("*lower_bound(L'b') = {0}",   
        *c1.lower_bound(L'b'));   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
lower_bound(L'x')==end() = True  
*lower_bound(L'a') = a  
*lower_bound(L'b') = b  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [Set (STL/CLR)](../dotnet/set-stl-clr.md)   
 [Set:: Count (STL/CLR)](../dotnet/set-count-stl-clr.md)   
 [Set:: equal_range (STL/CLR)](../dotnet/set-equal-range-stl-clr.md)   
 [Set:: Find (STL/CLR)](../dotnet/set-find-stl-clr.md)   
 [set::upper_bound (STL/CLR)](../dotnet/set-upper-bound-stl-clr.md)