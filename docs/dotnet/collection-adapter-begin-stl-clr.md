---
title: collection_adapter::begin (STL/CLR) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::collection_adapter::begin
dev_langs: C++
helpviewer_keywords: begin member [STL/CLR]
ms.assetid: fba55a3f-c1c6-4679-8c94-54cbb468e44c
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cedaf603f3d737f60bf1f1cbc1d18e7f2a13710f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="collectionadapterbegin-stlclr"></a>collection_adapter::begin (STL/CLR)
Designa el principio de la secuencia controlada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
iterator begin();  
```  
  
## <a name="remarks"></a>Comentarios  
 La función miembro devuelve un iterador de entrada que designa el primer elemento de la secuencia controlada o más allá del final de una secuencia vacía.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_collection_adapter_begin.cpp   
// compile with: /clr   
#include <cliext/adapter>   
#include <cliext/deque>   
  
typedef cliext::collection_adapter<   
    System::Collections::ICollection> Mycoll;   
int main()   
    {   
    cliext::deque<wchar_t> d1;   
    d1.push_back(L'a');   
    d1.push_back(L'b');   
    d1.push_back(L'c');   
    Mycoll c1(%d1);   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    Mycoll::iterator it = c1.begin();   
    System::Console::WriteLine("*begin() = {0}", *it);   
    System::Console::WriteLine("*++begin() = {0}", *++it);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*begin() = a  
*++begin() = b  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/adaptador >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [collection_adapter (STL/CLR)](../dotnet/collection-adapter-stl-clr.md)   
 [collection_adapter::end (STL/CLR)](../dotnet/collection-adapter-end-stl-clr.md)