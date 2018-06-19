---
title: 'List:: splice (STL/CLR) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::list::splice
dev_langs:
- C++
helpviewer_keywords:
- splice member [STL/CLR]
ms.assetid: ebc424b9-8341-4a88-b101-86d56324f5ac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e0c92faf6a4ec84e6ed65c58d02337038398d37e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33135955"
---
# <a name="listsplice-stlclr"></a>list::splice (STL/CLR)
Restitch vínculos entre nodos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void splice(iterator where, list<Value>% right);  
void splice(iterator where, list<Value>% right,  
    iterator first);  
void splice(iterator where, list<Value>% right,  
    iterator first, iterator last);  
```  
  
#### <a name="parameters"></a>Parámetros  
 first  
 Comienzo del intervalo que se va a unir.  
  
 last  
 Final del intervalo que se va a unir.  
  
 right  
 Contenedor que se va a unir de.  
  
 donde  
 WHERE contenedor splice antes.  
  
## <a name="remarks"></a>Comentarios  
 La primera función miembro inserta la secuencia controlada por `right` antes del elemento de la secuencia controlada señalada por `where`. También quita todos los elementos de `right`. (`%right` no deben ser iguales `this`.) Usa para splice todas de una lista a otro.  
  
 La segunda función miembro quita el elemento indicado por `first` en la secuencia controlada por `right` y lo inserta delante del elemento de la secuencia controlada que señala `where`. (Si `where` `==` `first` `||` `where` `== ++first`, se produce ningún cambio.) Se usar para insertar un único elemento de una lista a otro.  
  
 La tercera función miembro inserta el subintervalo designado por [`first`, `last`) de la secuencia controlada por `right` antes del elemento de la secuencia controlada señalada por `where`. También quita el subintervalo original de la secuencia controlada por `right`. (If `right` `==` `this`, el intervalo [`first`, `last`) no se debe incluir el elemento indicado por `where`.) Se usar para insertar una subsecuencia de cero o más elementos de una lista a otro.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_list_splice.cpp   
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
  
// splice to a new list   
    cliext::list<wchar_t> c2;   
    c2.splice(c2.begin(), c1);   
    System::Console::WriteLine("c1.size() = {0}", c1.size());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// return one element   
    c1.splice(c1.end(), c2, c2.begin());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// return remaining elements   
    c1.splice(c1.begin(), c2, c2.begin(), c2.end());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("c2.size() = {0}", c2.size());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
c1.size() = 0  
 a b c  
 a  
 b c  
 b c a  
c2.size() = 0  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/list >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [lista (STL/CLR)](../dotnet/list-stl-clr.md)   
 [List:: assign (STL/CLR)](../dotnet/list-assign-stl-clr.md)   
 [List:: Insert (STL/CLR)](../dotnet/list-insert-stl-clr.md)   
 [list::merge (STL/CLR)](../dotnet/list-merge-stl-clr.md)