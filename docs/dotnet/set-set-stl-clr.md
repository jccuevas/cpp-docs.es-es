---
title: 'Set:: Set (STL/CLR) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::set::set
dev_langs:
- C++
helpviewer_keywords:
- set member [STL/CLR]
ms.assetid: 0cce8501-92ed-431c-b711-14e0b7be7375
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6de8bb2616cd403e150ace02210e57ed5a019445
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33172607"
---
# <a name="setset-stlclr"></a>set::set (STL/CLR)
Construye un objeto contenedor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
set();  
explicit set(key_compare^ pred);  
set(set<Key>% right);  
set(set<Key>^ right);  
template<typename InIter>  
    setset(InIter first, InIter last);  
template<typename InIter>  
    set(InIter first, InIter last,  
        key_compare^ pred);  
set(System::Collections::Generic::IEnumerable<GValue>^ right);  
set(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred);  
```  
  
#### <a name="parameters"></a>Parámetros  
 first  
 Comienzo del intervalo que se va a insertar.  
  
 last  
 Final del intervalo que se va a insertar.  
  
 pred  
 Orden de predicado de la secuencia controlada.  
  
 right  
 Objeto o intervalo que se va a insertar.  
  
## <a name="remarks"></a>Comentarios  
 El constructor:  
  
 `set();`  
  
 Inicializa la secuencia controlada con ningún elemento con el predicado del orden predeterminado `key_compare()`. Se usa para especificar una secuencia controlada inicial vacía, con el predicado del orden predeterminado.  
  
 El constructor:  
  
 `explicit set(key_compare^ pred);`  
  
 Inicializa la secuencia controlada con ningún elemento con el predicado ordenación `pred`. Se usa para especificar una secuencia controlada inicial vacía, con el predicado de ordenación especificado.  
  
 El constructor:  
  
 `set(set<Key>% right);`  
  
 Inicializa la secuencia controlada a la secuencia [`right.begin()`, `right.end()`), con el predicado del orden predeterminado. Se usa para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto de conjunto `right`, con el predicado del orden predeterminado.  
  
 El constructor:  
  
 `set(set<Key>^ right);`  
  
 Inicializa la secuencia controlada a la secuencia [`right->begin()`, `right->end()`), con el predicado del orden predeterminado. Se usa para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto de conjunto `right`, con el predicado del orden predeterminado.  
  
 El constructor:  
  
 `template<typename InIter> set(InIter first, InIter last);`  
  
 Inicializa la secuencia controlada a la secuencia [`first`, `last`), con el predicado del orden predeterminado. Usa para hacer una copia de otra secuencia de la secuencia controlada con el predicado del orden predeterminado.  
  
 El constructor:  
  
 `template<typename InIter> set(InIter first, InIter last, key_compare^ pred);`  
  
 Inicializa la secuencia controlada a la secuencia [`first`, `last`), con el predicado ordenación `pred`. Usa para realizar una copia de otra secuencia, con el predicado especificado de ordenación de la secuencia controlada.  
  
 El constructor:  
  
 `set(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 Inicializa la secuencia controlada con la secuencia designada por el enumerador `right`, con el predicado del orden predeterminado. Usa para realizar una copia de otra secuencia descrita por un enumerador con el predicado del orden predeterminado de la secuencia controlada.  
  
 El constructor:  
  
 `set(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`  
  
 Inicializa la secuencia controlada con la secuencia designada por el enumerador `right`, con el predicado ordenación `pred`. Usa para realizar una copia de otra secuencia descrita por un enumerador con el predicado especificado de ordenación de la secuencia controlada.  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_set_construct.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
// construct an empty container   
    Myset c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Myset c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Myset c3(c1.begin(), c1.end());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Myset c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Myset c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Myset c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,   
            cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c6)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct from a generic container   
    Myset c7(c4);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Myset c8(%c3);   
    for each (wchar_t elem in c8)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 a b c  
size() = 0  
 c b a  
 a b c  
 c b a  
 a b c  
 c b a  
 c b a  
 a b c  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [Set (STL/CLR)](../dotnet/set-stl-clr.md)   
 [Set::generic_container (STL/CLR)](../dotnet/set-generic-container-stl-clr.md)   
 [set::operator= (STL/CLR)](../dotnet/set-operator-assign-stl-clr.md)