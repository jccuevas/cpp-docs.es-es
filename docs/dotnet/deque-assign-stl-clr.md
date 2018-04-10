---
title: deque (STL/CLR) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- cliext::deque::assign
dev_langs:
- C++
helpviewer_keywords:
- assign member [STL/CLR]
ms.assetid: 03fafdbb-6b10-4464-b3dc-0cc5cb8ac980
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1ae8bb7a21a336987d30cb41a7a1ff9d586db830
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="dequeassign-stlclr"></a>deque::assign (STL/CLR)
Reemplaza todos los elementos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void assign(size_type count, value_type val);  
template<typename InIt>  
    void assign(InIt first, InIt last);  
void assign(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `count`  
 Número de elementos que se van a insertar.  
  
 `first`  
 Comienzo del intervalo que se va a insertar.  
  
 `last`  
 Final del intervalo que se va a insertar.  
  
 `right`  
 Enumeración para insertar.  
  
 `val`  
 Valor del elemento que se va a insertar.  
  
## <a name="remarks"></a>Comentarios  
 La primera función miembro reemplaza la secuencia controlada por una repetición de `count` elementos del valor `val`. Usarlo para rellenar el contenedor con elementos de todos los que tengan el mismo valor.  
  
 Si `InIt` es de tipo entero, la segunda función miembro comporta igual que `assign((size_type)first, (value_type)last)`. En caso contrario, reemplaza la secuencia controlada por la secuencia [`first`, `last`). Usarlo para realizar el controlado de secuencia de una copia otra secuencia.  
  
 La tercera función miembro reemplaza la secuencia controlada por la secuencia designada por el enumerador `right`. Usa para realizar una copia de una secuencia descrita por un enumerador de la secuencia controlada.  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_deque_assign.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// assign a repetition of values   
    cliext::deque<wchar_t> c2;   
    c2.assign(6, L'x');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign an iterator range   
    c2.assign(c1.begin(), c1.end() - 1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign an enumeration   
    c2.assign(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
x x x x x x  
a b  
a b c  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/deque >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [deque (STL/CLR)](../dotnet/deque-stl-clr.md)   
 [operator= (deque) (STL/CLR)](../dotnet/operator-assign-deque-stl-clr.md)