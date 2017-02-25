---
title: "set::key_comp (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::set::key_comp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "key_comp (miembro) [STL/CLR]"
ms.assetid: 245db5d0-0610-4c68-a708-9bb99e48325c
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# set::key_comp (STL/CLR)
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
// cliext_set_key_comp.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    Myset::key_compare^ kcomp = c1.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Myset c2 = cliext::greater<wchar_t>();   
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
  
  **comparar \(L'a, L'a\) \= False**  
**comparar \(L'a, L'b\) \= True**  
**comparar \(L'b, L'a\) \= False**  
**comparar \(L'a, L'a\) \= False**  
**comparar \(L'a, L'b\) \= False**  
**comparar \(L'b, L'a\) \= True**   
## Requisitos  
 cliext \<o conjunto de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [set](../dotnet/set-stl-clr.md)   
 [set::key\_compare](../dotnet/set-key-compare-stl-clr.md)   
 [set::key\_type](../dotnet/set-key-type-stl-clr.md)