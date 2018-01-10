---
title: 'deque:: deque (STL/CLR) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::deque::deque
dev_langs: C++
helpviewer_keywords: deque member [STL/CLR]
ms.assetid: e5bc9511-619e-469c-b50a-e06858e7fce7
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b077e4c92d9307b8ff99126c824d0a902ce1ff83
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="dequedeque-stlclr"></a>deque::deque (STL/CLR)
Construye un objeto contenedor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
deque();  
deque(deque<Value>% right);  
deque(deque<Value>^ right);  
explicit deque(size_type count);  
deque(size_type count, value_type val);  
template<typename InIt>  
    deque(InIt first, InIt last);  
deque(System::Collections::Generic::IEnumerable<Value>^ right);  
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
  
 `deque();`  
  
 Inicializa la secuencia controlada con ningún elemento. Se usa para especificar una secuencia controlada inicial vacía.  
  
 El constructor:  
  
 `deque(deque<Value>% right);`  
  
 Inicializa la secuencia controlada a la secuencia [`right.begin()`, `right.end()`). Se usa para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto deque `right`. Para obtener más información sobre los iteradores, vea [deque (STL/CLR)](../dotnet/deque-begin-stl-clr.md) y [deque:: end (STL/CLR)](../dotnet/deque-end-stl-clr.md).  
  
 El constructor:  
  
 `deque(deque<Value>^ right);`  
  
 Inicializa la secuencia controlada a la secuencia [`right->begin()`, `right->end()`). Se usa para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto deque cuyo identificador es `right`.  
  
 El constructor:  
  
 `explicit deque(size_type count);`  
  
 Inicializa la secuencia controlada con `count` elementos con el valor `value_type()`. Usarlo para rellenar el contenedor con elementos de todos los que tiene el valor predeterminado.  
  
 El constructor:  
  
 `deque(size_type count, value_type val);`  
  
 Inicializa la secuencia controlada con `count` elementos con el valor `val`. Usarlo para rellenar el contenedor con elementos de todos los que tengan el mismo valor.  
  
 El constructor:  
  
 `template<typename InIt>`  
  
 `deque(InIt first, InIt last);`  
  
 Inicializa la secuencia controlada a la secuencia [`first`, `last`). Usa para realizar una copia de otra secuencia de la secuencia controlada.  
  
 El constructor:  
  
 `deque(System::Collections::Generic::IEnumerable<Value>^ right);`  
  
 Inicializa la secuencia controlada con la secuencia designada por el enumerador `right`. Usa para realizar una copia de otra secuencia descrita por un enumerador de la secuencia controlada.  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_deque_construct.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
// construct an empty container   
    cliext::deque<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct with a repetition of default values   
    cliext::deque<wchar_t> c2(3);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// construct with a repetition of values   
    cliext::deque<wchar_t> c3(6, L'x');   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    cliext::deque<wchar_t>::iterator it = c3.end();   
    cliext::deque<wchar_t> c4(c3.begin(), --it);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    cliext::deque<wchar_t> c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    cliext::deque<wchar_t> c7(c3);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    cliext::deque<wchar_t> c8(%c3);   
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
 **Encabezado:** \<cliext/deque >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [deque (STL/CLR)](../dotnet/deque-assign-stl-clr.md)   
 [deque::generic_container (STL/CLR)](../dotnet/deque-generic-container-stl-clr.md)   
 [operator= (deque) (STL/CLR)](../dotnet/operator-assign-deque-stl-clr.md)