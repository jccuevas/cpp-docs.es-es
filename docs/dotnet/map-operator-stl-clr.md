---
title: "map::operator(STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::map::operator[]"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator[] (miembro) [STL/CLR]"
ms.assetid: 50e494c5-62d4-4469-8da3-7432ee4dff97
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# map::operator(STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Asigna una clave a su valor asignado asociado.  
  
## Sintaxis  
  
```  
mapped_type operator[](key_type key);  
```  
  
#### Parámetros  
 clave  
 Valor de clave que se va a buscar.  
  
## Comentarios  
 Las funciones miembro los esfuerzos para encontrar un elemento con el equivalente de ordenación a `key`.  Si encuentra alguno, devuelve el valor asignado asociado; si no, inserta `value_type(``key``, mapped_type())` y devuelve \(valor predeterminado\) el valor asignado asociado.  Se utiliza para buscar un valor asignado dado su clave asociada, o para asegurarse de que una entrada existe para la clave si no se encuentra ninguno.  
  
## Ejemplo  
  
```  
// cliext_map_operator_sub.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("c1[{0}] = {1}",   
        L'A', c1[L'A']);   
    System::Console::WriteLine("c1[{0}] = {1}",   
        L'b', c1[L'b']);   
  
// redisplay altered contents   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// alter mapped values and redisplay   
    c1[L'A'] = 10;   
    c1[L'c'] = 13;   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **\[un 1\] \[b 2\] \[c 3\]**  
**c1 \[En\] \= 0**  
**c1 \[b\] \= 2**  
 **\[A 0\] \[un 1\] \[b 2\] \[c 3\]**  
 **\[A 10\] \[un 1\] \[b 2\] \[c 13\]**   
## Requisitos  
 cliext \<de**Encabezado:** \/asignado\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [map](../dotnet/map-stl-clr.md)   
 [map::find](../dotnet/map-find-stl-clr.md)   
 [map::insert](../dotnet/map-insert-stl-clr.md)