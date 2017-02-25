---
title: "set::key_compare (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::set::key_compare"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "key_compare (miembro) [STL/CLR]"
ms.assetid: 4ce14c96-24d7-48eb-ae78-4ab192f7422a
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# set::key_compare (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El delegado de ordenación para dos claves.  
  
## Sintaxis  
  
```  
Microsoft::VisualC::StlClr::BinaryDelegate<GKey, GKey, bool>  
    key_compare;  
```  
  
## Comentarios  
 El tipo es un sinónimo del delegado que determina el orden de sus argumentos clave.  
  
## Ejemplo  
  
```  
// cliext_set_key_compare.cpp   
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
 [set::key\_comp](../dotnet/set-key-comp-stl-clr.md)   
 [set::key\_type](../dotnet/set-key-type-stl-clr.md)   
 [set::value\_compare](../dotnet/set-value-compare-stl-clr.md)