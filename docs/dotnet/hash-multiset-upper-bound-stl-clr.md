---
title: "hash_multiset::upper_bound (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::hash_multiset::upper_bound"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "upper_bound (miembro) [STL/CLR]"
ms.assetid: d5be0d79-ae60-42bb-8a53-051bc374407d
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# hash_multiset::upper_bound (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Encuentra el final del intervalo que coincide con una clave especificada.  
  
## Sintaxis  
  
```  
iterator upper_bound(key_type key);  
```  
  
#### Parámetros  
 clave  
 Valor de clave que se va a buscar.  
  
## Comentarios  
 La función miembro determina el último elemento `X` en la secuencia controlada que aplica un algoritmo hash al mismo depósito que `key` y tiene equivalente de ordenación a `key`.  Si no existe ningún elemento, o si `X` es el último elemento de la secuencia controlada, devuelve [hash\_multiset::end](../dotnet/hash-multiset-end-stl-clr.md)`()`; si no devuelve un iterador que señala el primer elemento más allá de `X`.  Se utiliza para buscar el final de una secuencia de elementos actualmente en la secuencia controlada que coinciden con una clave especificada.  
  
## Ejemplo  
  
```  
// cliext_hash_multiset_upper_bound.cpp   
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
  
    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",   
        c1.upper_bound(L'x') == c1.end());   
  
    System::Console::WriteLine("*upper_bound(L'a') = {0}",   
        *c1.upper_bound(L'a'));   
    System::Console::WriteLine("*upper_bound(L'b') = {0}",   
        *c1.upper_bound(L'b'));   
    return (0);   
    }  
  
```  
  
  **a b c**  
**upper\_bound\(L'x'\)\=\=end\(\) \= True**  
**\*upper\_bound \(L'a\) \= b**  
**\*upper\_bound \(L'b\) \= c**   
## Requisitos  
 cliext \<\/hash\_set de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_multiset::count](../dotnet/hash-multiset-count-stl-clr.md)   
 [hash\_multiset::equal\_range](../dotnet/hash-multiset-equal-range-stl-clr.md)   
 [hash\_multiset::find](../dotnet/hash-multiset-find-stl-clr.md)   
 [hash\_multiset::lower\_bound](../dotnet/hash-multiset-lower-bound-stl-clr.md)