---
title: "list::list (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::list::list"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "lista de miembros [STL/CLR]"
ms.assetid: 51b58f63-c65a-4d54-b746-0c10635b123b
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# list::list (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Construye un objeto contenedor.  
  
## Sintaxis  
  
```  
list();  
list(list<Value>% right);  
list(list<Value>^ right);  
explicit list(size_type count);  
list(size_type count, value_type val);  
template<typename InIt>  
    list(InIt first, InIt last);  
list(System::Collections::Generic::IEnumerable<Value>^ right);  
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
  
 `list();`  
  
 inicializa la secuencia controlada sin elementos.  Se utiliza para especificar una secuencia controlada inicial vacía.  
  
 El constructor:  
  
 `list(list<Value>% right);`  
  
 inicializa la secuencia controlada con la secuencia `[``right``.`[list::begin](../dotnet/list-begin-stl-clr.md)`(),` `right``.`[list::end](../dotnet/list-end-stl-clr.md)`())`.  Se utiliza para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto `right`de la lista.  
  
 El constructor:  
  
 `list(list<Value>^ right);`  
  
 inicializa la secuencia controlada con la secuencia `[``right``->`[list::begin](../dotnet/list-begin-stl-clr.md)`(),` `right``->`[list::end](../dotnet/list-end-stl-clr.md)`())`.  Se utiliza para especificar una secuencia controlada inicial que es una copia de la secuencia controlada por el objeto de lista cuyo identificador es `right`.  
  
 El constructor:  
  
 `explicit list(size_type count);`  
  
 inicializa la secuencia controlada con elementos de `count` cada una con el valor `value_type()`.  Se utiliza para rellenar el contenedor con todos los elementos que tiene el valor predeterminado.  
  
 El constructor:  
  
 `list(size_type count, value_type val);`  
  
 inicializa la secuencia controlada con elementos de `count` cada una con el valor `val`.  Se utiliza para rellenar el contenedor con todos los elementos que tiene el mismo valor.  
  
 El constructor:  
  
 `template<typename InIt>`  
  
 `list(InIt first, InIt last);`  
  
 inicializa la secuencia controlada con la secuencia `[``first``,` `last``)`.  Se utiliza para hacer la secuencia controlada una copia de otra secuencia.  
  
 El constructor:  
  
 `list(System::Collections::Generic::IEnumerable<Value>^ right);`  
  
 inicializa la secuencia controlada con la secuencia indicada por el enumerador `right`.  Se utiliza para hacer la secuencia controlada una copia de otra secuencia descrita por un enumerador.  
  
## Ejemplo  
  
```  
// cliext_list_construct.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
// construct an empty container   
    cliext::list<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct with a repetition of default values   
    cliext::list<wchar_t> c2(3);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// construct with a repetition of values   
    cliext::list<wchar_t> c3(6, L'x');   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    cliext::list<wchar_t>::iterator it = c3.end();   
    cliext::list<wchar_t> c4(c3.begin(), --it);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    cliext::list<wchar_t> c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    cliext::list<wchar_t> c7(c3);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    cliext::list<wchar_t> c8(%c3);   
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
 cliext \<de**Encabezado:** \/enumerado\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [list](../dotnet/list-stl-clr.md)   
 [list::assign](../dotnet/list-assign-stl-clr.md)   
 [list::generic\_container](../dotnet/list-generic-container-stl-clr.md)   
 [list::operator\=](../dotnet/list-operator-assign-stl-clr.md)