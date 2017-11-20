---
title: Map (STL/CLR) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::map::map
dev_langs: C++
helpviewer_keywords: map member [STL/CLR]
ms.assetid: c91f699a-4742-4859-b2b3-c2a01a750bea
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d8fe3e0dd20ae07f3378bd528d7e19986c2aed6b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="mapmap-stlclr"></a>map::map (STL/CLR)
Construye un objeto contenedor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
map();  
explicit map(key_compare^ pred);  
map(map<Key, Mapped>% right);  
map(map<Key, Mapped>^ right);  
template<typename InIter>  
    mapmap(InIter first, InIter last);  
template<typename InIter>  
    map(InIter first, InIter last,  
        key_compare^ pred);  
map(System::Collections::Generic::IEnumerable<GValue>^ right);  
map(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred);  
```  
  
#### <a name="parameters"></a>Parámetros  
 first  
 Comienzo del intervalo que se va a insertar.  
  
 last  
 Final del intervalo que se va a insertar.  
  
 pred  
 Orden de predicado de la secuencia controlada.  
  
 derecha  
 Objeto o intervalo que se va a insertar.  
  
## <a name="remarks"></a>Comentarios  
 El constructor:  
  
 `map();`  
  
 Inicializa la secuencia controlada con ningún elemento con el predicado del orden predeterminado `key_compare()`. Se usa para especificar una secuencia controlada inicial vacía, con el predicado del orden predeterminado.  
  
 El constructor:  
  
 `explicit map(key_compare^ pred);`  
  
 Inicializa la secuencia controlada con ningún elemento con el predicado ordenación `pred`. Se usa para especificar una secuencia controlada inicial vacía, con el predicado de ordenación especificado.  
  
 El constructor:  
  
 `map(map<Key, Mapped>% right);`  
  
 Inicializa la secuencia controlada a la secuencia [`right.begin()`, `right.end()`), con el predicado del orden predeterminado. Se usa para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto de mapa `right`, con el predicado del orden predeterminado.  
  
 El constructor:  
  
 `map(map<Key, Mapped>^ right);`  
  
 Inicializa la secuencia controlada a la secuencia [`right->begin()`, `right->end()`), con el predicado del orden predeterminado. Se usa para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto de mapa `right`, con el predicado del orden predeterminado.  
  
 El constructor:  
  
 `template<typename InIter> map(InIter first, InIter last);`  
  
 Inicializa la secuencia controlada a la secuencia [`first`, `last`), con el predicado del orden predeterminado. Usa para hacer una copia de otra secuencia de la secuencia controlada con el predicado del orden predeterminado.  
  
 El constructor:  
  
 `template<typename InIter> map(InIter first, InIter last, key_compare^ pred);`  
  
 Inicializa la secuencia controlada a la secuencia [`first`, `last`), con el predicado ordenación `pred`. Usa para realizar una copia de otra secuencia, con el predicado especificado de ordenación de la secuencia controlada.  
  
 El constructor:  
  
 `map(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 Inicializa la secuencia controlada con la secuencia designada por el enumerador `right`, con el predicado del orden predeterminado. Usa para realizar una copia de otra secuencia descrita por un enumerador con el predicado del orden predeterminado de la secuencia controlada.  
  
 El constructor:  
  
 `map(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`  
  
 Inicializa la secuencia controlada con la secuencia designada por el enumerador `right`, con el predicado ordenación `pred`. Usa para realizar una copia de otra secuencia descrita por un enumerador con el predicado especificado de ordenación de la secuencia controlada.  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
// cliext_map_construct.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
// construct an empty container   
    Mymap c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Mymap c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (Mymap::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Mymap c3(c1.begin(), c1.end());   
    for each (Mymap::value_type elem in c3)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Mymap c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (Mymap::value_type elem in c4)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Mymap c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Mymap::value_type>^)%c3);   
    for each (Mymap::value_type elem in c5)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Mymap c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Mymap::value_type>^)%c3,   
                cliext::greater_equal<wchar_t>());   
    for each (Mymap::value_type elem in c6)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Mymap c7(c4);   
    for each (Mymap::value_type elem in c7)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    Mymap c8(%c3);   
    for each (Mymap::value_type elem in c8)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 [a 1] [b 2] [c 3]  
size() = 0  
 [c 3] [b 2] [a 1]  
 [a 1] [b 2] [c 3]  
 [c 3] [b 2] [a 1]  
 [a 1] [b 2] [c 3]  
 [c 3] [b 2] [a 1]  
 [c 3] [b 2] [a 1]  
 [a 1] [b 2] [c 3]  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/mapa >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [asignar (STL/CLR)](../dotnet/map-stl-clr.md)   
 [Map::generic_container (STL/CLR)](../dotnet/map-generic-container-stl-clr.md)   
 [map::operator= (STL/CLR)](../dotnet/map-operator-assign-stl-clr.md)