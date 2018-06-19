---
title: 'Set:: swap (STL/CLR) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::set::swap
dev_langs:
- C++
helpviewer_keywords:
- swap member [STL/CLR]
ms.assetid: c1733a77-d23f-44cb-b038-f1893a6fe6b1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6d7c05c56767fdd9b058b62d35bf218905c06418
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33171368"
---
# <a name="setswap-stlclr"></a>set::swap (STL/CLR)
Intercambia el contenido de dos contenedores.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void swap(set<Key>% right);  
```  
  
#### <a name="parameters"></a>Parámetros  
 right  
 Contenedor con el que se va a intercambiar el contenido.  
  
## <a name="remarks"></a>Comentarios  
 La función miembro intercambia las secuencias controladas entre `this` y `right`. Lo hace en tiempo constante y no inicia ninguna excepción. Utiliza como una forma rápida para intercambiar el contenido de dos contenedores.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_set_swap.cpp   
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
  
// construct another container with repetition of values   
    Myset c2;   
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
 [Set (STL/CLR)](../dotnet/set-stl-clr.md)   
 [set::operator= (STL/CLR)](../dotnet/set-operator-assign-stl-clr.md)