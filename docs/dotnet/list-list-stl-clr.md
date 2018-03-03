---
title: 'List:: List (STL/CLR) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::list::list
dev_langs:
- C++
helpviewer_keywords:
- list member [STL/CLR]
ms.assetid: 51b58f63-c65a-4d54-b746-0c10635b123b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2ae85dbdab7bb1d72862aa315949821ba5cdb830
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="listlist-stlclr"></a>list::list (STL/CLR)
Construye un objeto contenedor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
list();  
list(list<Value>% right);  
list(list<Value>^ right);  
explicit list(size_type count);  
list(size_type count, value_type val);  
template<typename InIt>  
    list(InIt first, InIt last);  
list(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `count`  
 Número de elementos que se van a insertar.  
  
 `first`  
 Comienzo del intervalo que se va a insertar.  
  
 `last`  
 Final del intervalo que se va a insertar.  
  
 `right`  
 Objeto o intervalo que se va a insertar.  
  
 `val`  
 Valor del elemento que se va a insertar.  
  
## <a name="remarks"></a>Comentarios  
  
 El constructor:  
  
 `list();`  
  
 Inicializa la secuencia controlada con ningún elemento. Se usa para especificar una secuencia controlada inicial vacía.  
  
 El constructor:  
  
 `list(list<Value>% right);`  
  
 Inicializa la secuencia controlada a la secuencia [`right.begin()`, `right.end()`). Se usa para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto de lista `right`.  
  
 El constructor:  
  
 `list(list<Value>^ right);`  
  
 Inicializa la secuencia controlada a la secuencia [`right->begin()`, `right->end()`). Se usa para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto de lista cuyo identificador es `right`.  
  
 El constructor:  
  
 `explicit list(size_type count);`  
  
 Inicializa la secuencia controlada con `count` elementos con el valor `value_type()`. Usarlo para rellenar el contenedor con elementos de todos los que tiene el valor predeterminado.  
  
 El constructor:  
  
 `list(size_type count, value_type val);`  
  
 Inicializa la secuencia controlada con `count` elementos con el valor `val`. Usarlo para rellenar el contenedor con elementos de todos los que tengan el mismo valor.  
  
 El constructor:  
  
 `template<typename InIt>`  
  
 `list(InIt first, InIt last);`  
  
 Inicializa la secuencia controlada a la secuencia [`first`, `last`). Usa para realizar una copia de otra secuencia de la secuencia controlada.  
  
 El constructor:  
  
 `list(System::Collections::Generic::IEnumerable<Value>^ right);`  
  
 Inicializa la secuencia controlada con la secuencia designada por el enumerador `right`. Usa para realizar una copia de otra secuencia descrita por un enumerador de la secuencia controlada.  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_list_construct.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
// construct an empty container   
    cliext::list<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct with a repetition of default values   
    cliext::list<wchar_t> c2(3);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// construct with a repetition of values   
    cliext::list<wchar_t> c3(6, L'x');   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    cliext::list<wchar_t>::iterator it = c3.end();   
    cliext::list<wchar_t> c4(c3.begin(), --it);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    cliext::list<wchar_t> c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    cliext::list<wchar_t> c7(c3);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    cliext::list<wchar_t> c8(%c3);   
    for each (wchar_t elem in c8)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 0 0 0  
 x x x x x x  
 x x x x x  
 x x x x x x  
 x x x x x x  
 x x x x x x  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/list >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [lista (STL/CLR)](../dotnet/list-stl-clr.md)   
 [List:: assign (STL/CLR)](../dotnet/list-assign-stl-clr.md)   
 [List::generic_container (STL/CLR)](../dotnet/list-generic-container-stl-clr.md)   
 [list::operator= (STL/CLR)](../dotnet/list-operator-assign-stl-clr.md)