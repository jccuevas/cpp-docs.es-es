---
title: 'MULTISET:: swap (STL/CLR) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::multiset::swap
dev_langs:
- C++
helpviewer_keywords:
- swap member [STL/CLR]
ms.assetid: 8a3023c7-e58b-4ffe-8fd5-2e0bf02cc291
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: af273d88f30cf514d6fa69df5604ea3e154d6681
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="multisetswap-stlclr"></a>multiset::swap (STL/CLR)
Intercambia el contenido de dos contenedores.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void swap(multiset<Key>% right);  
```  
  
#### <a name="parameters"></a>Parámetros  
 right  
 Contenedor con el que se va a intercambiar el contenido.  
  
## <a name="remarks"></a>Comentarios  
 La función miembro intercambia las secuencias controladas entre `this` y `right`. Lo hace en tiempo constante y no inicia ninguna excepción. Utiliza como una forma rápida para intercambiar el contenido de dos contenedores.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_multiset_swap.cpp   
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
  
// construct another container with repetition of values   
    Mymultiset c2;   
    c2.insert(L'd');   
    c2.insert(L'e');   
    c2.insert(L'f');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// swap and redisplay   
    c1.swap(c2);   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
d e f  
d e f  
a b c  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [MULTISET (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [multiset::operator= (STL/CLR)](../dotnet/multiset-operator-assign-stl-clr.md)