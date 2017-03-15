---
title: "hash_multiset::swap (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::hash_multiset::swap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "swap (miembro) [STL/CLR]"
ms.assetid: b79372ab-ca51-494a-89cf-4e2da3ee3ff7
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# hash_multiset::swap (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Intercambia el contenido de dos contenedores.  
  
## Sintaxis  
  
```  
void swap(hash_multiset<Key>% right);  
```  
  
#### Parámetros  
 right  
 Contenedor con el que se va a intercambiar el contenido.  
  
## Comentarios  
 La función miembro cambia las secuencias controladas entre `this` y `right`.  Hacerlo en tiempo constante y no produce ninguna excepción.  Se utiliza como una manera rápida de cambiar el contenido de dos contenedores.  
  
## Ejemplo  
  
```  
// cliext_hash_multiset_swap.cpp   
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
  
// construct another container with repetition of values   
    Myhash_multiset c2;   
    c2.insert(L'd');   
    c2.insert(L'e');   
    c2.insert(L'f');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// swap and redisplay   
    c1.swap(c2);   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
 **f de d e**  
 **f de d e**  
 **a b c**   
## Requisitos  
 cliext \<\/hash\_set de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_multiset::operator\=](../dotnet/hash-multiset-operator-assign-stl-clr.md)