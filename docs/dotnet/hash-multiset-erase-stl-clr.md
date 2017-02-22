---
title: "hash_multiset::erase (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::hash_multiset::erase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "erase (miembro) [STL/CLR]"
ms.assetid: bddd329d-aece-4b93-8355-005351c3aa45
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# hash_multiset::erase (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Quita los elementos en las posiciones especificadas.  
  
## Sintaxis  
  
```  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
bool erase(key_type key)  
```  
  
#### Parámetros  
 first  
 Inicio del intervalo que se va a borrar.  
  
 clave  
 Valor de clave que se va a borrar.  
  
 last  
 Final del intervalo que se va a borrar.  
  
 donde  
 Elemento que se va a borrar.  
  
## Comentarios  
 La primera función miembro quita el elemento de la secuencia controlada designada por a `where`, y devuelve un iterador que señala el primer elemento que permanece más allá del elemento quitado, o [hash\_multiset::end](../dotnet/hash-multiset-end-stl-clr.md)`()` si no existe ese elemento.  Se utiliza para quitar un solo elemento.  
  
 La segunda función miembro quita elementos de la secuencia controlada en el intervalo `[``first``,` `last``)`, y devuelve un iterador que señala el primer elemento que permanece más allá de cualquier elemento quitado, o `end()` si no existe ningún elemento.  Se utiliza para quitar elementos cero o más contiguo.  
  
 La tercera función miembro quita cualquier elemento de la secuencia controlada cuya clave tiene equivalente de ordenación a `key`, y devuelve el número de elementos eliminados.  Se utiliza para quitar y para contar todos los elementos que coinciden con una clave especificada.  
  
 Cada borradura de elemento lleva tiempo proporcional al logaritmo del número de elementos de la secuencia controlada.  
  
## Ejemplo  
  
```  
// cliext_hash_multiset_erase.cpp   
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
  
// erase an element and reinspect   
    System::Console::WriteLine("erase(begin()) = {0}",   
        *c1.erase(c1.begin()));   
  
// add elements and display " b c d e"   
    c1.insert(L'd');   
    c1.insert(L'e');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase all but end   
    Myhash_multiset::iterator it = c1.end();   
    System::Console::WriteLine("erase(begin(), end()-1) = {0}",   
        *c1.erase(c1.begin(), --it));   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
  **a b c**  
**erase\(begin\(\)\) \= b**  
 **d e de la b c**  
**erase\(begin\(\), end\(\)\-1\) \= e**  
**size\(\) \= 1**   
## Requisitos  
 cliext \<\/hash\_set de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_multiset::clear](../dotnet/hash-multiset-clear-stl-clr.md)