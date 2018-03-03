---
title: 'List:: Sort (STL/CLR) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::list::sort
dev_langs:
- C++
helpviewer_keywords:
- sort member [STL/CLR]
ms.assetid: f811d5f4-a19e-4194-8765-1e68097c52f0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 159391bc7d362c755c194f478692b2a271d779ed
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="listsort-stlclr"></a>list::sort (STL/CLR)
Ordena la secuencia controlada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void sort();  
template<typename Pred2>  
    void sort(Pred2 pred);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pred  
 Comparador para los pares de elemento.  
  
## <a name="remarks"></a>Comentarios  
 La primera función miembro reorganiza los elementos de la secuencia controlada para que se ordenan por `operator<` --elementos no disminuyen en valor a medida que avanza a través de la secuencia. Utilice esta función miembro para ordenar la secuencia en orden ascendente.  
  
 La segunda función miembro comporta igual que la primera, salvo que la secuencia está ordenada por `pred`  --  `pred(X, Y)` es false para cualquier elemento `X` que sigue elemento `Y` en la secuencia resultante. Usa para ordenar la secuencia en un orden que se especifica por una función de predicado o un delegado.  
  
 Las funciones realizan a una ordenación estable, ningún par de elementos de la secuencia controlada original se ha invertido en la secuencia controlada resultante.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_list_sort.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// sort descending and redisplay   
    c1.sort(cliext::greater<wchar_t>());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// sort ascending and redisplay   
    c1.sort();   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
c b a  
a b c  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/list >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [lista (STL/CLR)](../dotnet/list-stl-clr.md)   
 [List:: Merge (STL/CLR)](../dotnet/list-merge-stl-clr.md)   
 [List:: Reverse (STL/CLR)](../dotnet/list-reverse-stl-clr.md)   
 [List:: splice (STL/CLR)](../dotnet/list-splice-stl-clr.md)   
 [list::unique (STL/CLR)](../dotnet/list-unique-stl-clr.md)