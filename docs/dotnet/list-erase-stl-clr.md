---
title: 'List:: Erase (STL/CLR) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::list::erase
dev_langs:
- C++
helpviewer_keywords:
- erase member [STL/CLR]
ms.assetid: 78705058-1e83-441d-b267-d4fb56451c0b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 080cfbca2a69db9e277e080f5c34206b08e89c69
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="listerase-stlclr"></a>list::erase (STL/CLR)
Quita los elementos de las posiciones especificadas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
```  
  
#### <a name="parameters"></a>Parámetros  
 first  
 Comienzo del intervalo que se va a borrar.  
  
 last  
 Final del intervalo que se va a borrar.  
  
 donde  
 Elemento que se va a borrar.  
  
## <a name="remarks"></a>Comentarios  
 La primera función miembro quita el elemento de la secuencia controlada señalada por `where`. Usa para quitar un único elemento.  
  
 La segunda función miembro quita los elementos de la secuencia controlada en el intervalo [`first`, `last`). Usa para quitar cero o más elementos contiguos.  
  
 Ambas funciones miembro devuelven un iterador que designa el primer elemento que permanece más allá de los elementos quitados, o [List:: end (STL/CLR)](../dotnet/list-end-stl-clr.md) `()` si no existe ese elemento.  
  
 Al borrar los elementos, el número de copias del elemento es lineal en el número de elementos entre el final de la eliminación y el final cuanto más cerca de la secuencia. (Al borrar uno o más elementos en cualquier extremo de la secuencia, se produce ninguna copia del elemento.)  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_list_erase.cpp   
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
  
// erase an element and reinspect   
    System::Console::WriteLine("erase(begin()) = {0}",   
        *c1.erase(c1.begin()));   
  
// add elements and display " b c d e"   
    c1.push_back(L'd');   
    c1.push_back(L'e');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase all but end   
    cliext::list<wchar_t>::iterator it = c1.end();   
    System::Console::WriteLine("erase(begin(), end()-1) = {0}",   
        *c1.erase(c1.begin(), --it));   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
erase(begin()) = b  
 b c d e  
erase(begin(), end()-1) = e  
size() = 1  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/list >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [lista (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list::clear (STL/CLR)](../dotnet/list-clear-stl-clr.md)