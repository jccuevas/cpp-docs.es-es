---
title: "deque::deque (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::deque::deque"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "deque (miembro) [STL/CLR]"
ms.assetid: e5bc9511-619e-469c-b50a-e06858e7fce7
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# deque::deque (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Construye un objeto contenedor.  
  
## Sintaxis  
  
```  
deque();  
deque(deque<Value>% right);  
deque(deque<Value>^ right);  
explicit deque(size_type count);  
deque(size_type count, value_type val);  
template<typename InIt>  
    deque(InIt first, InIt last);  
deque(System::Collections::Generic::IEnumerable<Value>^ right);  
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
  
 `deque();`  
  
 inicializa la secuencia controlada sin elementos.  Se utiliza para especificar una secuencia controlada inicial vacía.  
  
 El constructor:  
  
 `deque(deque<Value>% right);`  
  
 inicializa la secuencia controlada con la secuencia `[``right``.`[deque::begin](../dotnet/deque-begin-stl-clr.md)`(),` `right``.`[deque::end](../dotnet/deque-end-stl-clr.md)`())`.  Se utiliza para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto `right`de deque.  
  
 El constructor:  
  
 `deque(deque<Value>^ right);`  
  
 inicializa la secuencia controlada con la secuencia `[``right``->`[deque::begin](../dotnet/deque-begin-stl-clr.md)`(),` `right``->`[deque::end](../dotnet/deque-end-stl-clr.md)`())`.  Se utiliza para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto de deque cuyo identificador es `right`.  
  
 El constructor:  
  
 `explicit deque(size_type count);`  
  
 inicializa la secuencia controlada con elementos de `count` cada una con el valor `value_type()`.  Se utiliza para rellenar el contenedor con todos los elementos que tiene el valor predeterminado.  
  
 El constructor:  
  
 `deque(size_type count, value_type val);`  
  
 inicializa la secuencia controlada con elementos de `count` cada una con el valor `val`.  Se utiliza para rellenar el contenedor con todos los elementos que tiene el mismo valor.  
  
 El constructor:  
  
 `template<typename InIt>`  
  
 `deque(InIt first, InIt last);`  
  
 inicializa la secuencia controlada con la secuencia `[``first``,` `last``)`.  Se utiliza para hacer la secuencia controlada una copia de otra secuencia.  
  
 El constructor:  
  
 `deque(System::Collections::Generic::IEnumerable<Value>^ right);`  
  
 inicializa la secuencia controlada con la secuencia indicada por el enumerador `right`.  Se utiliza para hacer la secuencia controlada una copia de otra secuencia descrita por un enumerador.  
  
## Ejemplo  
  
```  
// cliext_deque_construct.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
// construct an empty container   
    cliext::deque<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct with a repetition of default values   
    cliext::deque<wchar_t> c2(3);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// construct with a repetition of values   
    cliext::deque<wchar_t> c3(6, L'x');   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    cliext::deque<wchar_t>::iterator it = c3.end();   
    cliext::deque<wchar_t> c4(c3.begin(), --it);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    cliext::deque<wchar_t> c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    cliext::deque<wchar_t> c7(c3);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    cliext::deque<wchar_t> c8(%c3);   
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
 **Encabezado:** \<cliext\/deque\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [deque](../dotnet/deque-stl-clr.md)   
 [deque::assign](../dotnet/deque-assign-stl-clr.md)   
 [deque::generic\_container](../dotnet/deque-generic-container-stl-clr.md)   
 [operator\= \(deque\)](../dotnet/operator-assign-deque-stl-clr.md)