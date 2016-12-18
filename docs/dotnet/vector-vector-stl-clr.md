---
title: "vector::vector (STL/CLR) | Microsoft Docs"
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
  - "cliext::vector::vector"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "vector (miembro) [STL/CLR]"
ms.assetid: a0b5e807-1ef2-422b-b772-1f96cd62fb51
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# vector::vector (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Construye un objeto contenedor.  
  
## Sintaxis  
  
```  
vector();  
vector(vector<Value>% right);  
vector(vector<Value>^ right);  
explicit vector(size_type count);  
vector(size_type count, value_type val);  
template<typename InIt>  
    vector(InIt first, InIt last);  
vector(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### Parámetros  
 count  
 Número de elementos que se va a insertar.  
  
 first  
 Inicio del intervalo que se va a insertar.  
  
 last  
 Final del intervalo que se va a insertar.  
  
 right  
 Objeto o intervalo para insertar.  
  
 val  
 Valor del elemento que se va a insertar.  
  
## Comentarios  
 El constructor:  
  
 `vector();`  
  
 inicializa la secuencia controlada sin elementos.  Se utiliza para especificar una secuencia controlada inicial vacía.  
  
 El constructor:  
  
 `vector(vector<Value>% right);`  
  
 inicializa la secuencia controlada con la secuencia `[``right``.`[vector::begin](../dotnet/vector-begin-stl-clr.md)`(),` `right``.`[vector::end](../dotnet/vector-end-stl-clr.md)`())`.  Se utiliza para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto `right`vectoriales.  
  
 El constructor:  
  
 `vector(vector<Value>^ right);`  
  
 inicializa la secuencia controlada con la secuencia `[``right``->`[vector::begin](../dotnet/vector-begin-stl-clr.md)`(),` `right``->`[vector::end](../dotnet/vector-end-stl-clr.md)`())`.  Se utiliza para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto vector cuyo identificador es `right`.  
  
 El constructor:  
  
 `explicit vector(size_type count);`  
  
 inicializa la secuencia controlada con elementos de `count` cada una con el valor `value_type()`.  Se utiliza para rellenar el contenedor con todos los elementos que tiene el valor predeterminado.  
  
 El constructor:  
  
 `vector(size_type count, value_type val);`  
  
 inicializa la secuencia controlada con elementos de `count` cada una con el valor `val`.  Se utiliza para rellenar el contenedor con todos los elementos que tiene el mismo valor.  
  
 El constructor:  
  
 `template<typename InIt>`  
  
 `vector(InIt first, InIt last);`  
  
 inicializa la secuencia controlada con la secuencia `[``first``,` `last``)`.  Se utiliza para hacer la secuencia controlada una copia de otra secuencia.  
  
 El constructor:  
  
 `vector(System::Collections::Generic::IEnumerable<Value>^ right);`  
  
 inicializa la secuencia controlada con la secuencia indicada por el enumerador `right`.  Se utiliza para hacer la secuencia controlada una copia de otra secuencia descrita por un enumerador.  
  
## Ejemplo  
  
```  
// cliext_vector_construct.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
// construct an empty container   
    cliext::vector<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct with a repetition of default values   
    cliext::vector<wchar_t> c2(3);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// construct with a repetition of values   
    cliext::vector<wchar_t> c3(6, L'x');   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    cliext::vector<wchar_t>::iterator it = c3.end();   
    cliext::vector<wchar_t> c4(c3.begin(), --it);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    cliext::vector<wchar_t> c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    cliext::vector<wchar_t> c7(c3);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    cliext::vector<wchar_t> c8(%c3);   
    for each (wchar_t elem in c8)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
  
```  
  
  **size\(\) \= 0**  
 **0 0 0**  
 **x x x x x x**  
 **x x x x x**  
 **x x x x x x**  
 **x x x x x x**  
 **x x x x x x**   
## Requisitos  
 cliext \<\/vector de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [vector](../dotnet/vector-stl-clr.md)   
 [vector::assign](../dotnet/vector-assign-stl-clr.md)   
 [vector::generic\_container](../dotnet/vector-generic-container-stl-clr.md)   
 [vector::operator\=](../dotnet/vector-operator-assign-stl-clr.md)