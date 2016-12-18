---
title: "set::make_value (STL/CLR) | Microsoft Docs"
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
  - "cliext::set::make_value"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "make_value (miembro) [STL/CLR]"
ms.assetid: 2f71515e-7de1-4139-a68e-72ff2a96aa4a
caps.latest.revision: 8
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# set::make_value (STL/CLR)
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
// cliext_set_make_value.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
int main()   
    {   
    Myset c1;   
    c1.insert(Myset::make_value(L'a'));   
    c1.insert(Myset::make_value(L'b'));   
    c1.insert(Myset::make_value(L'c'));   
  
// display contents " a b c"   
    for each (Myset::value_type elem in c1)   
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
 [set](../dotnet/set-stl-clr.md)   
 [set::key\_type](../dotnet/set-key-type-stl-clr.md)   
 [set::value\_type](../dotnet/set-value-type-stl-clr.md)