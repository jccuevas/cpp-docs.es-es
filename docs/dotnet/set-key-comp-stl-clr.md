---
title: key_comp (STL/CLR) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::set::key_comp
dev_langs: C++
helpviewer_keywords: key_comp member [STL/CLR]
ms.assetid: 245db5d0-0610-4c68-a708-9bb99e48325c
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: af382d0e8c14ecdc16419604d7cd31346fadcfa9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="setkeycomp-stlclr"></a>set::key_comp (STL/CLR)
Copia al delegado para dos claves de ordenación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
key_compare^key_comp();  
```  
  
## <a name="remarks"></a>Comentarios  
 La función miembro devuelve al delegado de ordenación utilizado para ordenar la secuencia controlada. Usa para comparar dos claves.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_set_key_comp.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    Myset::key_compare^ kcomp = c1.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Myset c2 = cliext::greater<wchar_t>();   
    kcomp = c2.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    return (0);   
    }  
  
```  
  
```Output  
compare(L'a', L'a') = False  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
  
compare(L'a', L'a') = False  
compare(L'a', L'b') = False  
compare(L'b', L'a') = True  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [Set (STL/CLR)](../dotnet/set-stl-clr.md)   
 [Set:: key_compare (STL/CLR)](../dotnet/set-key-compare-stl-clr.md)   
 [set::key_type (STL/CLR)](../dotnet/set-key-type-stl-clr.md)