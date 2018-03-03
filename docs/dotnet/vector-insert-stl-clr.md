---
title: 'Vector:: Insert (STL/CLR) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::vector::insert
dev_langs:
- C++
helpviewer_keywords:
- insert member [STL/CLR]
ms.assetid: f240cabf-f9d1-40c1-9cfb-975a90955546
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b330a9e0b8a11f41ceab4f604b73b93e8f1d735a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="vectorinsert-stlclr"></a>vector::insert (STL/CLR)
Agrega un elemento en una posición especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
iterator insert(iterator where, value_type val);  
void insert(iterator where, size_type count, value_type val);  
template<typename InIt>  
    void insert(iterator where, InIt first, InIt last);  
void insert(iterator where,  
    System::Collections::Generic::IEnumerable<Value>^ right);  
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
  
 donde  
 WHERE en el contenedor para insertar antes.  
  
## <a name="remarks"></a>Comentarios  
 Cada uno de los miembros funciones inserta, antes del elemento señalado por `where` en la secuencia controlada, una secuencia especificada por los operandos restantes.  
  
 La primera función miembro inserta un elemento con el valor `val` y devuelve un iterador que designa el elemento recién insertado. Se usar para insertar un elemento único antes de un lugar designado por un iterador.  
  
 La segunda función miembro inserta una repetición de `count` elementos de valor `val`. Usa para insertar cero o más elementos contiguos que son todas las copias del mismo valor.  
  
 Si `InIt` es un tipo entero, la tercera función miembro se comporta igual que `insert(where, (size_type)first, (value_type)last)`. En caso contrario, inserta la secuencia [`first`, `last`). Usa para insertar cero o más elementos contiguos copiados desde otra secuencia.  
  
 La cuarta función miembro inserta la secuencia designada por el `right`. Usa para insertar una secuencia descrita por un enumerador.  
  
 Cuando se inserta un elemento único, el número de copias del elemento es lineal en el número de elementos entre el punto de inserción y el final cuanto más cerca de la secuencia. (Cuando se inserta uno o más elementos en cualquier extremo de la secuencia, se produce ninguna copia del elemento.) Si `InIt` es un iterador de entrada, la tercera función miembro realiza una inserción única para cada elemento de la secuencia. En caso contrario, al insertar `N` elementos, el número de copias del elemento es lineal en `N` más el número de elementos entre el punto de inserción y el final cuanto más cerca de la secuencia.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_vector_insert.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value using iterator   
    cliext::vector<wchar_t>::iterator it = c1.begin();   
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",   
        *c1.insert(++it, L'x'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a repetition of values   
    cliext::vector<wchar_t> c2;   
    c2.insert(c2.begin(), 2, L'y');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    it = c1.end();   
    c2.insert(c2.end(), c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    c2.insert(c2.begin(),   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
insert(begin()+1, L'x') = x  
 a x b c  
 y y  
 y y a x b  
 a x b c y y a x b  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/vector >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [vector (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [vector::assign (STL/CLR)](../dotnet/vector-assign-stl-clr.md)