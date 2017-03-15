---
title: "vector::capacity (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::vector::capacity"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "capacity (miembro) [STL/CLR]"
ms.assetid: f82d8da9-8b4d-4288-8d18-8e9ca5911d87
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# vector::capacity (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Notifica el tamaño de almacenamiento asignado del contenedor.  
  
## Sintaxis  
  
```  
size_type capacity();  
```  
  
## Comentarios  
 La función miembro devuelve almacenamiento asignado actualmente para la secuencia controlada, un valor por lo menos tan grande como [vector::size](../dotnet/vector-size-stl-clr.md)`()`.  Se utiliza para determinar cuánto puede llegar al contenedor antes de que debe reasignar el almacenamiento para la secuencia controlada.  
  
## Ejemplo  
  
```  
// cliext_vector_capacity.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1.at(i));   
    System::Console::WriteLine();   
  
// increase capacity   
    cliext::vector<wchar_t>::size_type cap = c1.capacity();   
    System::Console::WriteLine("capacity() = {0}, ok = {1}",   
        cap, c1.size() <= cap);   
    c1.reserve(cap + 5);   
    System::Console::WriteLine("capacity() = {0}, ok = {1}",   
        c1.capacity(), cap + 5 <= c1.capacity());   
    return (0);   
    }  
  
```  
  
  **a b c**  
**capacity\(\) \= 4, aceptable \= True**  
**capacity\(\) \= 9, aceptable \= True**   
## Descripción  
 Observe que las funciones reales pueden diferir de los valores que se muestran aquí, siempre y cuando todos los informes de pruebas de `ok` true.  
  
## Requisitos  
 cliext \<\/vector de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [vector](../dotnet/vector-stl-clr.md)   
 [vector::reserve](../dotnet/vector-reserve-stl-clr.md)