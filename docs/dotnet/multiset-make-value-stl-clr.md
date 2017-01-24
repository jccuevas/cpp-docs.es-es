---
title: "multiset::make_value (STL/CLR) | Microsoft Docs"
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
  - "cliext::multiset::make_value"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "make_value (miembro) [STL/CLR]"
ms.assetid: 385ded5b-65bf-4806-8c3d-a4129a05f612
caps.latest.revision: 8
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# multiset::make_value (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Construye un objeto value.  
  
## Sintaxis  
  
```  
static value_type make_value(key_type key);  
```  
  
#### Parámetros  
 clave  
 Valor de clave a utilizar.  
  
## Comentarios  
 La función miembro devuelve un objeto de `value_type` cuya clave se `key`.  Se utiliza para crear un objeto adecuado para el uso con otras funciones miembro.  
  
## Ejemplo  
  
```  
// cliext_multiset_make_value.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(Mymultiset::make_value(L'a'));   
    c1.insert(Mymultiset::make_value(L'b'));   
    c1.insert(Mymultiset::make_value(L'c'));   
  
// display contents " a b c"   
    for each (Mymultiset::value_type elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**   
## Requisitos  
 cliext \<o conjunto de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [multiset](../dotnet/multiset-stl-clr.md)   
 [multiset::key\_type](../dotnet/multiset-key-type-stl-clr.md)   
 [multiset::value\_type](../dotnet/multiset-value-type-stl-clr.md)