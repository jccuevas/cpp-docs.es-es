---
title: operador == (lista) (STL/CLR) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::list::operator==
dev_langs: C++
helpviewer_keywords: operator== member [STL/CLR]
ms.assetid: b290f7df-1bcd-44a5-a89e-925a0fcb8c65
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b198c9a46666e1d344512e7cb391b0f1883be6ca
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="operator-list-stlclr"></a>operator== (list) (STL/CLR)
Lista comparación igual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template<typename Value>  
    bool operator==(list<Value>% left,  
        list<Value>% right);  
```  
  
#### <a name="parameters"></a>Parámetros  
 izquierda  
 Contenedor izquierdo que se va a comparar.  
  
 derecha  
 Contenedor derecho que se va a comparar.  
  
## <a name="remarks"></a>Comentarios  
 La función de operador devuelve true solo si controlan las secuencias de `left` y `right` tienen la misma longitud y, para cada posición `i`, `left[i] ==` `right[i]`. Se usa para comprobar si `left` se ordenan igual `right` cuando las dos listas son comparado elemento por elemento.  
  
## <a name="example"></a>Ejemplo  
  
```  
// cliext_list_operator_eq.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::list<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] == [a b c] is {0}",   
        c1 == c1);   
    System::Console::WriteLine("[a b c] == [a b d] is {0}",   
        c1 == c2);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
 a b d  
[a b c] == [a b c] is True  
[a b c] == [a b d] is False  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<cliext/list >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Vea también  
 [lista (STL/CLR)](../dotnet/list-stl-clr.md)   
 [operador! = (list) (STL/CLR)](../dotnet/operator-inequality-list-stl-clr.md)   
 [operador\< (lista) (STL/CLR)](../dotnet/operator-less-than-list-stl-clr.md)   
 [operador > = (list) (STL/CLR)](../dotnet/operator-greater-or-equal-list-stl-clr.md)   
 [operador > (list) (STL/CLR)](../dotnet/operator-greater-than-list-stl-clr.md)   
 [operator<= (list) (STL/CLR)](../dotnet/operator-less-or-equal-list-stl-clr.md)