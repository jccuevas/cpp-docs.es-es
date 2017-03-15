---
title: "hash_set::key_comp (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::hash_set::key_comp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "key_comp (miembro) [STL/CLR]"
ms.assetid: d5dc46c3-c2ee-4591-8f03-d8c9d3df0519
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# hash_set::key_comp (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Copia el delegado de ordenación para dos claves.  
  
## Sintaxis  
  
```  
key_compare^key_comp();  
```  
  
## Comentarios  
 La función miembro devuelve el delegado de ordenación utilizado para ordenar la secuencia controlada.  Se usa para comparar dos claves.  
  
## Ejemplo  
  
```  
// cliext_hash_set_key_comp.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    Myhash_set::key_compare^ kcomp = c1.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Myhash_set c2 = cliext::greater<wchar_t>();   
    kcomp = c2.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    return (0);   
    }  
  
```  
  
  **comparar \(L'a, L'a\) \= True**  
**comparar \(L'a, L'b\) \= True**  
**comparar \(L'b, L'a\) \= False**  
**comparar \(L'a, L'a\) \= False**  
**comparar \(L'a, L'b\) \= False**  
**comparar \(L'b, L'a\) \= True**   
## Requisitos  
 cliext \<\/hash\_set de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [hash\_set](../dotnet/hash-set-stl-clr.md)   
 [hash\_set::key\_compare](../dotnet/hash-set-key-compare-stl-clr.md)   
 [hash\_set::key\_type](../dotnet/hash-set-key-type-stl-clr.md)