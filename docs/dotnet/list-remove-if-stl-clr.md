---
title: "list::remove_if (STL/CLR) | Microsoft Docs"
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
  - "cliext::list::remove_if"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "remove_if (miembro) [STL/CLR]"
ms.assetid: cbc66192-751b-41c5-b557-d5d7bbc2a840
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# list::remove_if (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Quita los elementos que pasan una prueba especificada.  
  
## Sintaxis  
  
```  
template<typename Pred1>  
    void remove_if(Pred1 pred);  
```  
  
#### Parámetros  
 pred  
 Pruebas para elementos quitar.  
  
## Comentarios  
 La función miembro quita de la secuencia controlada \(desactivada\) cada elemento `X` para el que `pred``(X)` sea true.  Se utiliza para quitar todos los elementos que satisfacen una condición especificada como una función o delegado.  
  
## Ejemplo  
  
```  
// cliext_list_remove_if.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'b');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b b b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// fail to remove and redisplay   
    c1.remove_if(cliext::binder2nd<cliext::equal_to<wchar_t> >(   
        cliext::equal_to<wchar_t>(), L'd'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// remove and redisplay   
    c1.remove_if(cliext::binder2nd<cliext::not_equal_to<wchar_t> >(   
        cliext::not_equal_to<wchar_t>(), L'b'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **una b c b b**  
 **una b c b b**  
 **b b b**   
## Requisitos  
 cliext \<de**Encabezado:** \/enumerado\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [list](../dotnet/list-stl-clr.md)   
 [list::clear](../dotnet/list-clear-stl-clr.md)   
 [list::erase](../dotnet/list-erase-stl-clr.md)   
 [list::remove](../dotnet/list-remove-stl-clr.md)   
 [list::unique](../dotnet/list-unique-stl-clr.md)