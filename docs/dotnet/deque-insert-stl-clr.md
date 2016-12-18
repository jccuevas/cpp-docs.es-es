---
title: "deque::insert (STL/CLR) | Microsoft Docs"
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
  - "cliext::deque::insert"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "insert (miembro) [STL/CLR]"
ms.assetid: a3b86c46-e6a8-42d0-b642-5a8f05ddd68c
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# deque::insert (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Agrega elementos en una posición especificada.  
  
## Sintaxis  
  
```  
iterator insert(iterator where, value_type val);  
void insert(iterator where, size_type count, value_type val);  
template<typename InIt>  
    void insert(iterator where, InIt first, InIt last);  
void insert(iterator where,  
    System::Collections::Generic::IEnumerable<Value>^ right);  
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
  
 donde  
 Donde en el contenedor insertar antes.  
  
## Comentarios  
 Cada una de las funciones miembro inserta, antes del elemento indicada por `where` en la secuencia controlada, una secuencia especificada por los operandos restantes.  
  
 La primera función miembro inserta un elemento con el valor `val` y devuelve un iterador que señala el elemento insertado recientemente.  Se utiliza para insertar un único elemento antes de un lugar designado por un iterador.  
  
 La segunda función miembro inserta una repetición de `count` elementos de valor `val`.  Se utiliza para insertar elementos cero o más contiguo que son todas las copias del mismo valor.  
  
 Si `InIt` es un tipo entero, la tercera función miembro se comporta igual que `insert(``where``, (size_type)``first``, (value_type)``last``)`.  Si no, inserte la secuencia `[``first``,` `last``)`.  Se utiliza para insertar elementos cero o más contiguo copiados de otra secuencia.  
  
 La cuarta función miembro inserta la secuencia indicada por `right`.  Se utiliza para insertar una secuencia descrita por un enumerador.  
  
 Al insertar un elemento único, el número de copias del elemento es lineal del número de elementos entre el punto de inserción y el final más próximo de la secuencia. \(Al incrustar uno o más elementos en el final de la secuencia, ninguna copia del elemento aparece.\) Si `InIt` es un iterador de entrada, la tercera función miembro realiza eficazmente una sola inserción para cada elemento de la secuencia.  Si no, al insertar los elementos de `N` , el número de copias del elemento es lineal en `N` más el número de elementos entre el punto de inserción y el final más próximo de la secuencia.  
  
## Ejemplo  
  
```  
// cliext_deque_insert.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value using iterator   
    cliext::deque<wchar_t>::iterator it = c1.begin();   
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",   
        *c1.insert(++it, L'x'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a repetition of values   
    cliext::deque<wchar_t> c2;   
    c2.insert(c2.begin(), 2, L'y');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    it = c1.end();   
    c2.insert(c2.end(), c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    c2.insert(c2.begin(),   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
**insert\(begin\(\)\+1, L'x\) \= x**  
 **una b c de x**  
 **e y**  
 **e y a b de x**  
 **una y la y la a b c de x a b de x**   
## Requisitos  
 **Encabezado:** \<cliext\/deque\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [deque](../dotnet/deque-stl-clr.md)   
 [deque::assign](../dotnet/deque-assign-stl-clr.md)