---
title: 'Vector:: Clear (STL/CLR) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::vector::clear
dev_langs: C++
helpviewer_keywords: clear member [STL/CLR]
ms.assetid: 4ed20ec8-3089-4c36-b68f-1b51c639041f
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8b03883d25aed8528d972cbc3569c67c56b83df2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="vectorclear-stlclr"></a>vector::clear (STL/CLR)
Quita todos los elementos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void clear();  
```  
  
## <a name="remarks"></a>Comentarios  
 La función miembro llama eficazmente a [vector:: Erase (STL/CLR)](../dotnet/vector-erase-stl-clr.md) `(` [vector:: begin (STL/CLR)](../dotnet/vector-begin-stl-clr.md) `(),` [vector:: end (STL/CLR)](../dotnet/vector-end-stl-clr.md) `())`. Utilizarlo para asegurarse de que la secuencia controlada está vacía.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_vector_clear.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// add elements and clear again   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
  
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
 **Encabezado:** \<cliext/vector >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [vector (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [vector::erase (STL/CLR)](../dotnet/vector-erase-stl-clr.md)