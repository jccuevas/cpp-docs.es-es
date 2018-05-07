---
title: 'Set:: value_comp (STL/CLR) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::set::value_comp
dev_langs:
- C++
helpviewer_keywords:
- value_comp member [STL/CLR]
ms.assetid: 3b7e469d-ca73-415b-bd20-24968c51107c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 614855867c548a1faf86c8971d1d3646b39ee16e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="setvaluecomp-stlclr"></a>set::value_comp (STL/CLR)
Copia al delegado de ordenación para los dos valores de elemento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
value_compare^ value_comp();  
```  
  
## <a name="remarks"></a>Comentarios  
 La función miembro devuelve al delegado de ordenación utilizado para ordenar la secuencia controlada. Usa para comparar dos valores de elemento.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_set_value_comp.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    Myset::value_compare^ kcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
compare(L'a', L'a') = False  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [Set (STL/CLR)](../dotnet/set-stl-clr.md)   
 [Set:: value_compare (STL/CLR)](../dotnet/set-value-compare-stl-clr.md)   
 [set::value_type (STL/CLR)](../dotnet/set-value-type-stl-clr.md)