---
title: 'List:: UNIQUE (STL/CLR) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::list::unique
dev_langs: C++
helpviewer_keywords: unique member [STL/CLR]
ms.assetid: c3a29e4e-0ec1-4472-b050-7a9511037132
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ca78fcc1de8b579a647dd9080dc64db0fde54e9b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="listunique-stlclr"></a>list::unique (STL/CLR)
Quita los elementos adyacentes que superan una prueba especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void unique();  
template<typename Pred2>  
    void unique(Pred2 pred);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pred  
 Comparador para los pares de elemento.  
  
## <a name="remarks"></a>Comentarios  
 La primera función miembro quita de la secuencia controlada (borrados) igual a todos los elementos que se comparan con el elemento anterior--si elemento `X` preceda elemento `Y` y `X == Y`, la función miembro quita `Y`. Se usa para quitar todo menos una copia de cada subsecuencia de los elementos adyacentes que compare igual. Tenga en cuenta que si se ordena la secuencia controlada, tal como mediante una llamada a [List:: Sort (STL/CLR)](../dotnet/list-sort-stl-clr.md)`()`, la función miembro deja sólo los elementos con valores únicos. (Por lo tanto, el nombre).  
  
 La segunda función miembro comporta igual que la primera, salvo que quita cada elemento `Y` después de un elemento `X` que `pred(X, Y)`. Usa para quitar todo menos una copia de cada subsecuencia de elementos adyacentes que cumplan una función de predicado o un delegado que especifique. Tenga en cuenta que si se ordena la secuencia controlada, tal como mediante una llamada a `sort(pred)`, la función miembro deja sólo los elementos que no tienen una ordenación equivalente con otros elementos.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_list_unique.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display contents after unique   
    cliext::list<wchar_t> c2(c1);   
    c2.unique();   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display contents after unique(not_equal_to)   
    c2 = c1;   
    c2.unique(cliext::not_equal_to<wchar_t>());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a a b c  
a b c  
a a  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/list >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [lista (STL/CLR)](../dotnet/list-stl-clr.md)   
 [List:: Remove (STL/CLR)](../dotnet/list-remove-stl-clr.md)   
 [List:: remove_if (STL/CLR)](../dotnet/list-remove-if-stl-clr.md)   
 [list::sort (STL/CLR)](../dotnet/list-sort-stl-clr.md)