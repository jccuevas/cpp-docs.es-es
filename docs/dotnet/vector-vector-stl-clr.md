---
title: vector (STL/CLR) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::vector::vector
dev_langs: C++
helpviewer_keywords: vector member [STL/CLR]
ms.assetid: a0b5e807-1ef2-422b-b772-1f96cd62fb51
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: df28ca626eb8fde827f6c5c356848b37421fa797
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="vectorvector-stlclr"></a>vector::vector (STL/CLR)
Construye un objeto contenedor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
vector();  
vector(vector<Value>% right);  
vector(vector<Value>^ right);  
explicit vector(size_type count);  
vector(size_type count, value_type val);  
template<typename InIt>  
    vector(InIt first, InIt last);  
vector(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>Parámetros  
 count  
 Número de elementos que se van a insertar.  
  
 first  
 Comienzo del intervalo que se va a insertar.  
  
 last  
 Final del intervalo que se va a insertar.  
  
 derecha  
 Objeto o intervalo que se va a insertar.  
  
 Val  
 Valor del elemento que se va a insertar.  
  
## <a name="remarks"></a>Comentarios  
 El constructor:  
  
 `vector();`  
  
 Inicializa la secuencia controlada con ningún elemento. Se usa para especificar una secuencia controlada inicial vacía.  
  
 El constructor:  
  
 `vector(vector<Value>% right);`  
  
 Inicializa la secuencia controlada a la secuencia [`right.begin()`, `right.end()`). Se usa para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto de vector `right`.  
  
 El constructor:  
  
 `vector(vector<Value>^ right);`  
  
 Inicializa la secuencia controlada a la secuencia [`right->begin()`, `right->end()`). Se usa para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto de vector cuyo identificador es `right`.  
  
 El constructor:  
  
 `explicit vector(size_type count);`  
  
 Inicializa la secuencia controlada con `count` elementos con el valor `value_type()`. Usarlo para rellenar el contenedor con elementos de todos los que tiene el valor predeterminado.  
  
 El constructor:  
  
 `vector(size_type count, value_type val);`  
  
 Inicializa la secuencia controlada con `count` elementos con el valor `val`. Usarlo para rellenar el contenedor con elementos de todos los que tengan el mismo valor.  
  
 El constructor:  
  
 `template<typename InIt>`  
  
 `vector(InIt first, InIt last);`  
  
 Inicializa la secuencia controlada a la secuencia [`first`, `last`). Usa para realizar una copia de otra secuencia de la secuencia controlada.  
  
 El constructor:  
  
 `vector(System::Collections::Generic::IEnumerable<Value>^ right);`  
  
 Inicializa la secuencia controlada con la secuencia designada por el enumerador `right`. Usa para realizar una copia de otra secuencia descrita por un enumerador de la secuencia controlada.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_vector_construct.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
// construct an empty container   
    cliext::vector<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct with a repetition of default values   
    cliext::vector<wchar_t> c2(3);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// construct with a repetition of values   
    cliext::vector<wchar_t> c3(6, L'x');   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    cliext::vector<wchar_t>::iterator it = c3.end();   
    cliext::vector<wchar_t> c4(c3.begin(), --it);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    cliext::vector<wchar_t> c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    cliext::vector<wchar_t> c7(c3);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    cliext::vector<wchar_t> c8(%c3);   
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
 **Encabezado:** \<cliext/vector >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [vector (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [Vector:: assign (STL/CLR)](../dotnet/vector-assign-stl-clr.md)   
 [Vector::generic_container (STL/CLR)](../dotnet/vector-generic-container-stl-clr.md)   
 [vector::operator= (STL/CLR)](../dotnet/vector-operator-assign-stl-clr.md)