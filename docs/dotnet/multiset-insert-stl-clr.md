---
title: "multiset::insert (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::multiset::insert"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "insert (miembro) [STL/CLR]"
ms.assetid: 7a3b1cc8-ec60-4ed0-ace5-46cb5872e6e7
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# multiset::insert (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Agrega elementos.  
  
## Sintaxis  
  
```  
iterator insert(value_type val);  
iterator insert(iterator where, value_type val);  
template<typename InIter>  
    void insert(InIter first, InIter last);  
void insert(System::Collections::Generic::IEnumerable<value_type>^ right);  
```  
  
#### Parámetros  
 first  
 Inicio del intervalo que se va a insertar.  
  
 last  
 Final del intervalo que se va a insertar.  
  
 right  
 Enumeración que se va a insertar.  
  
 val  
 Valor de clave que se va a insertar.  
  
 donde  
 Donde en el contenedor insertar \(sugerencia sólo\).  
  
## Comentarios  
 Cada una de las funciones miembro inserta una secuencia especificada por los operandos restantes.  
  
 La primera función miembro inserta un elemento con el valor `val`, y devuelve un iterador que señala el elemento insertado recientemente.  Se utiliza para insertar un solo elemento.  
  
 La segunda función miembro inserta un elemento con el valor `val`, mediante `where` como sugerencia \(mejorar rendimiento\), y devuelve un iterador que señala el elemento insertado recientemente.  Se utiliza para insertar un solo elemento que podría estar junto a un elemento que sabe.  
  
 La tercera función miembro inserta la secuencia `[``first``,` `last``)`.  Se utiliza para insertar cero o más elementos copiado de otra secuencia.  
  
 La cuarta función miembro inserta la secuencia indicada por `right`.  Se utiliza para insertar una secuencia descrita por un enumerador.  
  
 Cada inserción de elementos lleva tiempo proporcional al logaritmo del número de elementos de la secuencia controlada.  Inserción puede aparecer en el tiempo constante amortizado, sin embargo, dada una sugerencia que señale un elemento adyacente al punto de inserción.  
  
## Ejemplo  
  
```  
// cliext_multiset_insert.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value, unique and duplicate   
    System::Console::WriteLine("insert(L'x') = {0}",   
        *c1.insert(L'x'));   
  
    System::Console::WriteLine("insert(L'b') = {0}",   
        *c1.insert(L'b'));   
  
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value with hint   
    System::Console::WriteLine("insert(begin(), L'y') = {0}",   
        *c1.insert(c1.begin(), L'y'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    Mymultiset c2;   
    Mymultiset::iterator it = c1.end();   
    c2.insert(c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    Mymultiset c3;   
    c3.insert(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
**inserción \(L'x\) \= x**  
**inserción \(L'b\) \= b**  
 **una c x b b**  
**insert\(begin\(\), L'y\) \= y**  
 **una y c x b b**  
 **una c x b b**  
 **una y c x b b**   
## Requisitos  
 cliext \<o conjunto de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [multiset](../dotnet/multiset-stl-clr.md)