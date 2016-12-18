---
title: "set::insert (STL/CLR) | Microsoft Docs"
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
  - "cliext::set::insert"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "insert (miembro) [STL/CLR]"
ms.assetid: 40472869-5c28-4658-b1d3-3ede4d8b8921
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# set::insert (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Agrega elementos.  
  
## Sintaxis  
  
```  
cliext::pair<iterator, bool> insert(value_type val);  
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
  
 La primera función miembro se esfuerza para insertar un elemento con el valor `val`, y devuelve un par de valores `X`.  Si `X.second` es true, `X.first` designa el elemento insertado recientemente; si no `X.first` designa un elemento con equivalente solicitando que ya existe y no se insertará ningún nuevo elemento.  Se utiliza para insertar un solo elemento.  
  
 La segunda función miembro inserta un elemento con el valor `val`, mediante `where` como sugerencia \(mejorar rendimiento\), y devuelve un iterador que señala el elemento insertado recientemente.  Se utiliza para insertar un solo elemento que podría estar junto a un elemento que sabe.  
  
 La tercera función miembro inserta la secuencia `[``first``,` `last``)`.  Se utiliza para insertar cero o más elementos copiado de otra secuencia.  
  
 La cuarta función miembro inserta la secuencia indicada por `right`.  Se utiliza para insertar una secuencia descrita por un enumerador.  
  
 Cada inserción de elementos lleva tiempo proporcional al logaritmo del número de elementos de la secuencia controlada.  Inserción puede aparecer en el tiempo constante amortizado, sin embargo, dada una sugerencia que señale un elemento adyacente al punto de inserción.  
  
## Ejemplo  
  
```  
// cliext_set_insert.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::set<wchar_t> Myset;   
typedef Myset::pair_iter_bool Pairib;   
int main()   
    {   
    Myset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value, unique and duplicate   
    Pairib pair1 = c1.insert(L'x');   
    System::Console::WriteLine("insert(L'x') = [{0} {1}]",   
        *pair1.first, pair1.second);   
  
    pair1 = c1.insert(L'b');   
    System::Console::WriteLine("insert(L'b') = [{0} {1}]",   
        *pair1.first, pair1.second);   
  
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
    Myset c2;   
    Myset::iterator it = c1.end();   
    c2.insert(c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    Myset c3;   
    c3.insert(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **a b c**  
**inserción \(L'x\) \= \[x True\]**  
**inserción \(L'b\) \= \[b False\]**  
 **una c x b**  
**insert\(begin\(\), L'y\) \= y**  
 **una y c x b**  
 **una c x b**  
 **una y c x b**   
## Requisitos  
 cliext \<o conjunto de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [set](../dotnet/set-stl-clr.md)