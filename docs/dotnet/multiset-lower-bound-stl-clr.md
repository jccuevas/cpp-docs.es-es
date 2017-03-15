---
title: "multiset::lower_bound (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::multiset::lower_bound"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "lower_bound (miembro) [STL/CLR]"
ms.assetid: 5e3d1ba0-8b03-436e-b502-dbdb764f452b
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# multiset::lower_bound (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Encuentra el inicio del intervalo que coincide con una clave especificada.  
  
## Sintaxis  
  
```  
iterator lower_bound(key_type key);  
```  
  
#### Parámetros  
 clave  
 Valor de clave que se va a buscar.  
  
## Comentarios  
 La función miembro determina el primer elemento `X` en la secuencia controlada que tiene equivalente de ordenación a `key`.  Si no existe ningún elemento, devuelve [multiset::end](../dotnet/multiset-end-stl-clr.md)`()`; si no devuelve un iterador que señala `X`.  Se utiliza para buscar el principio de una secuencia de elementos actualmente en la secuencia controlada que coinciden con una clave especificada.  
  
## Ejemplo  
  
```  
// cliext_multiset_lower_bound.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",   
        c1.lower_bound(L'x') == c1.end());   
  
    System::Console::WriteLine("*lower_bound(L'a') = {0}",   
        *c1.lower_bound(L'a'));   
    System::Console::WriteLine("*lower_bound(L'b') = {0}",   
        *c1.lower_bound(L'b'));   
    return (0);   
    }  
  
```  
  
  **a b c**  
**lower\_bound\(L'x'\)\=\=end\(\) \= True**  
**\*lower\_bound \(L'a\) \= a**  
**\*lower\_bound \(L'b\) \= b**   
## Requisitos  
 cliext \<o conjunto de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [multiset](../dotnet/multiset-stl-clr.md)   
 [multiset::count](../dotnet/multiset-count-stl-clr.md)   
 [multiset::equal\_range](../dotnet/multiset-equal-range-stl-clr.md)   
 [multiset::find](../dotnet/multiset-find-stl-clr.md)   
 [multiset::upper\_bound](../dotnet/multiset-upper-bound-stl-clr.md)