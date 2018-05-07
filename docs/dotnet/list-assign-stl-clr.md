---
title: 'List:: assign (STL/CLR) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::list::assign
dev_langs:
- C++
helpviewer_keywords:
- assign member [STL/CLR]
ms.assetid: c5f2b131-d0e1-4188-9d4b-d617280e4032
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 02b579038d8945423d18d856e0682fe22245c563
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="listassign-stlclr"></a>list::assign (STL/CLR)
Reemplaza todos los elementos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void assign(size_type count, value_type val);  
template<typename InIt>  
    void assign(InIt first, InIt last);  
void assign(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>Parámetros  
 count  
 Número de elementos que se van a insertar.  
  
 first  
 Comienzo del intervalo que se va a insertar.  
  
 last  
 Final del intervalo que se va a insertar.  
  
 right  
 Enumeración para insertar.  
  
 Val  
 Valor del elemento que se va a insertar.  
  
## <a name="remarks"></a>Comentarios  
 La primera función miembro reemplaza la secuencia controlada por una repetición de `count` elementos del valor `val`. Usarlo para rellenar el contenedor con elementos de todos los que tengan el mismo valor.  
  
 Si `InIt` es de tipo entero, la segunda función miembro comporta igual que `assign((size_type)first, (value_type)last)`. En caso contrario, reemplaza la secuencia controlada por la secuencia [`first`, `last`). Usarlo para realizar el controlado de secuencia de una copia otra secuencia.  
  
 La tercera función miembro reemplaza la secuencia controlada por la secuencia designada por el enumerador `right`. Usa para realizar una copia de una secuencia descrita por un enumerador de la secuencia controlada.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_list_assign.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// assign a repetition of values   
    cliext::list<wchar_t> c2;   
    c2.assign(6, L'x');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign an iterator range   
    cliext::list<wchar_t>::iterator it = c1.end();   
    c2.assign(c1.begin(), --it);   
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
 **Encabezado:** \<cliext/list >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [lista (STL/CLR)](../dotnet/list-stl-clr.md)   
 [list::operator= (STL/CLR)](../dotnet/list-operator-assign-stl-clr.md)