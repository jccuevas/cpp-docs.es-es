---
title: 'List:: Resize (STL/CLR) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::list::resize
dev_langs:
- C++
helpviewer_keywords:
- resize member [STL/CLR]
ms.assetid: c4b8d41f-a62b-4dbc-8568-0e0a9da24016
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: bc9a883c2bd645713d631365675cfd7fd302d53e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33133615"
---
# <a name="listresize-stlclr"></a>list::resize (STL/CLR)
Cambia el número de elementos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void resize(size_type new_size);  
void resize(size_type new_size, value_type val);  
```  
  
#### <a name="parameters"></a>Parámetros  
 NEW_SIZE  
 Nuevo tamaño de la secuencia controlada.  
  
 Val  
 Valor del elemento de relleno.  
  
## <a name="remarks"></a>Comentarios  
 Las funciones de miembro tanto asegúrese de que [List:: Size (STL/CLR)](../dotnet/list-size-stl-clr.md) `()` de ahora en adelante devuelve `new_size`. Si la secuencia controlada tiene que ser más larga, la primera función miembro anexa elementos con el valor `value_type()`, mientras que la segunda función miembro anexa elementos con el valor `val`. Para realizar la secuencia controlada más corta, ambas funciones miembro borrar eficazmente el último elemento [List:: Size (STL/CLR)](../dotnet/list-size-stl-clr.md) `() -` `new_size` veces. Úsela para asegurarse de que la secuencia controlada tiene tamaño `new_size`, recortar o relleno de la secuencia controlada actual.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_list_resize.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
// construct an empty container and pad with default values   
    cliext::list<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
    c1.resize(4);   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// resize to empty   
    c1.resize(0);   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// resize and pad   
    c1.resize(5, L'x');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 0 0 0 0  
size() = 0  
 x x x x x  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/list >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [lista (STL/CLR)](../dotnet/list-stl-clr.md)   
 [List:: Clear (STL/CLR)](../dotnet/list-clear-stl-clr.md)   
 [List:: Erase (STL/CLR)](../dotnet/list-erase-stl-clr.md)   
 [list::insert (STL/CLR)](../dotnet/list-insert-stl-clr.md)