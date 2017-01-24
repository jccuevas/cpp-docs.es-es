---
title: "map::key_compare (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::map::key_compare"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "key_compare (miembro) [STL/CLR]"
ms.assetid: 6cde0e22-f1cb-4b92-b76d-bab6cbd9c825
caps.latest.revision: 14
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# map::key_compare (STL/CLR)
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
// cliext_map_key_compare.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    Mymap::key_compare^ kcomp = c1.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Mymap c2 = cliext::greater<wchar_t>();   
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
 cliext \<de**Encabezado:** \/asignado\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [map](../dotnet/map-stl-clr.md)   
 [map::key\_comp](../dotnet/map-key-comp-stl-clr.md)   
 [map::key\_type](../dotnet/map-key-type-stl-clr.md)   
 [map::value\_compare](../dotnet/map-value-compare-stl-clr.md)