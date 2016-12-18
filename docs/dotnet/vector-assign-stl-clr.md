---
title: "vector::assign (STL/CLR) | Microsoft Docs"
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
  - "cliext::vector::assign"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "assign (miembro) [STL/CLR]"
ms.assetid: 945e2048-6c61-4701-b13c-8241cbee3fa1
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# vector::assign (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Reemplaza todos los elementos.  
  
## Sintaxis  
  
```  
void assign(size_type count, value_type val);  
template<typename InIt>  
    void assign(InIt first, InIt last);  
void assign(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### Parámetros  
 count  
 Número de elementos que se va a insertar.  
  
 first  
 Inicio del intervalo que se va a insertar.  
  
 last  
 Final del intervalo que se va a insertar.  
  
 right  
 Enumeración que se va a insertar.  
  
 val  
 Valor del elemento que se va a insertar.  
  
## Comentarios  
 La primera función miembro reemplaza la secuencia controlada con una repetición de los elementos de `count` de valor `val`.  Se utiliza para rellenar el contenedor con todos los elementos que tiene el mismo valor.  
  
 Si `InIt` es un tipo entero, la segunda función miembro se comporta igual que `assign((size_type)``first``, (value_type)``last``)`.  Si no, reemplace la secuencia controlada con la secuencia `[``first``,` `last``)`.  Se utiliza para hacer la secuencia controlada una copia otra secuencia.  
  
 La tercera función miembro reemplaza la secuencia controlada con la secuencia indicada por el enumerador `right`.  Se utiliza para hacer la secuencia controlada una copia de una secuencia descrita por un enumerador.  
  
## Ejemplo  
  
```  
// cliext_vector_assign.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// assign a repetition of values   
    cliext::vector<wchar_t> c2;   
    c2.assign(6, L'x');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign an iterator range   
    c2.assign(c1.begin(), c1.end() - 1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign an enumeration   
    c2.assign(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **x x x x x x**  
 **una b**  
 **a b c**   
## Requisitos  
 cliext \<\/vector de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [vector](../dotnet/vector-stl-clr.md)   
 [vector::operator\=](../dotnet/vector-operator-assign-stl-clr.md)