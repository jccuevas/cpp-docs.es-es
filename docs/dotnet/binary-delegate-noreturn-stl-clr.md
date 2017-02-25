---
title: "binary_delegate_noreturn (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::binary_delegate_noreturn"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "binary_delegate_noreturn (función) [STL/CLR]"
ms.assetid: 055c7e9d-e5c3-48fe-9327-3f6316e8a51e
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# binary_delegate_noreturn (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase genereic describe un delegado de dos\- argumento que devuelve `void`.  Se utiliza especifica un delegado en términos de su argumento.  
  
## Sintaxis  
  
```  
generic<typename Arg1,  
    typename Arg2>  
    delegate void binary_delegate(Arg1, Arg2);  
```  
  
#### Parámetros  
 Arg1  
 El tipo del primer argumento.  
  
 Arg2  
 El tipo del segundo argumento.  
  
## Comentarios  
 El delegado genereic describe una función de dos\- argumento que devuelve `void`.  
  
 Observe que para:  
  
 `binary_delegate_noreturn<int, int> Fun1;`  
  
 `binary_delegate_noreturn<int, int> Fun2;`  
  
 los tipos `Fun1` y `Fun2` son sinónimos, mientras que para:  
  
 `delegate void Fun1(int, int);`  
  
 `delegate void Fun2(int, int);`  
  
 no son el mismo tipo.  
  
## Ejemplo  
  
```  
// cliext_binary_delegate_noreturn.cpp   
// compile with: /clr   
#include <cliext/functional>   
  
void key_compare(wchar_t left, wchar_t right)   
    {   
    System::Console::WriteLine("compare({0}, {1}) = {2}",   
        left, right, left < right);   
    }   
  
typedef cliext::binary_delegate_noreturn<wchar_t, wchar_t> Mydelegate;   
int main()   
    {   
    Mydelegate^ kcomp = gcnew Mydelegate(&key_compare);   
  
    kcomp(L'a', L'a');   
    kcomp(L'a', L'b');   
    kcomp(L'b', L'a');   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **comparar \(a,\) \= False**  
**comparar \(a, b\) \= True**  
**comparar \(b, a\) \= False**   
## Requisitos  
 cliext \<de**Encabezado:** \/funcional\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [binary\_delegate](../dotnet/binary-delegate-stl-clr.md)   
 [unary\_delegate](../dotnet/unary-delegate-stl-clr.md)   
 [unary\_delegate\_noreturn](../dotnet/unary-delegate-noreturn-stl-clr.md)