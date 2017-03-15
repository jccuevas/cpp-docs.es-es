---
title: "vector::erase (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::vector::erase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "erase (miembro) [STL/CLR]"
ms.assetid: 624905eb-83c0-499b-a07a-c10aebd7acc3
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# vector::erase (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Quita los elementos en las posiciones especificadas.  
  
## Sintaxis  
  
```  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
```  
  
#### Parámetros  
 first  
 Inicio del intervalo que se va a borrar.  
  
 last  
 Final del intervalo que se va a borrar.  
  
 donde  
 Elemento que se va a borrar.  
  
## Comentarios  
 La primera función miembro quita el elemento de la secuencia controlada designada por a `where`.  Se utiliza para quitar un solo elemento.  
  
 La segunda función miembro quita elementos de la secuencia controlada en el intervalo `[``first``,` `last``)`.  Se utiliza para quitar elementos cero o más contiguo.  
  
 Las funciones miembro devuelven un iterador que señala el primer elemento que permanece más allá de cualquier elemento quitado, o [vector::end](../dotnet/vector-end-stl-clr.md)`()` si no existe ese elemento.  
  
 Al borrar elementos, el número de copias del elemento es lineal del número de elementos entre el final de la borradura y el final más próximo de la secuencia. \(Al desactivar uno o más elementos en el final de la secuencia, ninguna copia del elemento aparece.\)  
  
## Ejemplo  
  
```  
// cliext_vector_erase.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase an element and reinspect   
    System::Console::WriteLine("erase(begin()) = {0}",   
        *c1.erase(c1.begin()));   
  
// add elements and display " b c d e"   
    c1.push_back(L'd');   
    c1.push_back(L'e');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase all but end   
    cliext::vector<wchar_t>::iterator it = c1.end();   
    System::Console::WriteLine("erase(begin(), end()-1) = {0}",   
        *c1.erase(c1.begin(), --it));   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
  **a b c**  
**erase\(begin\(\)\) \= b**  
 **d e de la b c**  
**erase\(begin\(\), end\(\)\-1\) \= e**  
**size\(\) \= 1**   
## Requisitos  
 cliext \<\/vector de**Encabezado:** \>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [vector](../dotnet/vector-stl-clr.md)   
 [vector::clear](../dotnet/vector-clear-stl-clr.md)