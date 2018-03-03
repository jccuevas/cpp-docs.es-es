---
title: 'hash_multiset:: Insert (STL/CLR) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::hash_multiset::insert
dev_langs:
- C++
helpviewer_keywords:
- insert member [STL/CLR]
ms.assetid: e7254f30-a514-4ddc-bf53-38aafbe9e8eb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3e309fa84ad67b7148ae92d95fa083c24173b6c8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="hashmultisetinsert-stlclr"></a>hash_multiset::insert (STL/CLR)
Agrega elementos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
iterator insert(value_type val);  
iterator insert(iterator where, value_type val);  
template<typename InIter>  
    void insert(InIter first, InIter last);  
void insert(System::Collections::Generic::IEnumerable<value_type>^ right);  
```  
  
#### <a name="parameters"></a>Parámetros  
 first  
 Comienzo del intervalo que se va a insertar.  
  
 last  
 Final del intervalo que se va a insertar.  
  
 right  
 Enumeración para insertar.  
  
 Val  
 Valor de clave para insertar.  
  
 donde  
 WHERE en el contenedor para insertar (solo sugerencia).  
  
## <a name="remarks"></a>Comentarios  
 Cada una de las funciones miembro inserta una secuencia especificada por los operandos restantes.  
  
 La primera función miembro inserta un elemento con el valor `val`y devuelve un iterador que designa el elemento recién insertado. Se usar para insertar un elemento único.  
  
 La segunda función miembro inserta un elemento con el valor `val`con `where` como una sugerencia (para mejorar el rendimiento) y devuelve un iterador que designa el elemento recién insertado. Se usar para insertar un elemento único que podría estar adyacente a un elemento que se conoce.  
  
 La tercera función miembro inserta la secuencia [`first`, `last`). Usa para insertar cero o más de los elementos copiados desde otra secuencia.  
  
 La cuarta función miembro inserta la secuencia designada por el `right`. Usa para insertar una secuencia descrita por un enumerador.  
  
 Cada inserción elemento lleva tiempo proporcional al logaritmo del número de elementos de la secuencia controlada. Inserción se puede realizar en tiempo constante amortizado, sin embargo, dada una sugerencia que designa un elemento adyacente al punto de inserción.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_hash_multiset_insert.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value, unique and duplicate   
    System::Console::WriteLine("insert(L'x') = {0}",   
        *c1.insert(L'x'));   
  
    System::Console::WriteLine("insert(L'b') = {0}",   
        *c1.insert(L'b'));   
  
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value with hint   
    System::Console::WriteLine("insert(begin(), L'y') = {0}",   
        *c1.insert(c1.begin(), L'y'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    Myhash_multiset c2;   
    Myhash_multiset::iterator it = c1.end();   
    c2.insert(c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    Myhash_multiset c3;   
    c3.insert(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
insert(L'x') = x  
insert(L'b') = b  
 a b b c x  
insert(begin(), L'y') = y  
 a b b c x y  
 a b b c x  
 a b b c x y  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/hash_set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)