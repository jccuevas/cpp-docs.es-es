---
title: "unary_delegate_noreturn (STL/CLR) | Microsoft Docs"
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
  - "cliext::unary_delegate_noreturn"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unary_delegate_noreturn (función) [STL/CLR]"
ms.assetid: 3c3fb143-f60f-4e28-a66b-690e3a7b2f9b
caps.latest.revision: 8
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# unary_delegate_noreturn (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase genereic describe un delegado de uno\- argumento que devuelve `void`.  Se utiliza especifica un delegado en términos del tipo de argumento.  
  
## Sintaxis  
  
```  
generic<typename Arg>  
    delegate void unary_delegate_noreturn(Arg);  
```  
  
#### Parámetros  
 Argumento  
 Tipo del argumento.  
  
## Comentarios  
 El delegado genereic describe una función de uno\- argumento que devuelve `void`.  
  
 Observe que para:  
  
 `unary_delegare_noreturn<int> Fun1;`  
  
 `unary_delegare_noreturn<int> Fun2;`  
  
 los tipos `Fun1` y `Fun2` son sinónimos, mientras que para:  
  
 `delegate void Fun1(int);`  
  
 `delegate void Fun2(int);`  
  
 no son el mismo tipo.  
  
## Ejemplo  
  
```  
// cliext_unary_delegate_noreturn.cpp   
// compile with: /clr   
#include <cliext/functional>   
  
void hash_val(wchar_t val)   
    {   
    System::Console::WriteLine("hash({0}) = {1}",   
       val, (val * 17 + 31) % 67);   
    }   
  
typedef cliext::unary_delegate_noreturn<wchar_t> Mydelegate;   
int main()   
    {   
    Mydelegate^ myhash = gcnew Mydelegate(&hash_val);   
  
    myhash(L'a');   
    myhash(L'b');   
    return (0);   
    }  
  
```  
  
  **hash \(a\) \= 5**  
**hash \(b\) \= 22**   
## Requisitos  
 cliext \<de**Encabezado:** \/funcional\>  
  
 cliext de**Espacio de nombres:**  
  
## Vea también  
 [binary\_delegate](../dotnet/binary-delegate-stl-clr.md)   
 [binary\_delegate\_noreturn](../dotnet/binary-delegate-noreturn-stl-clr.md)   
 [unary\_delegate](../dotnet/unary-delegate-stl-clr.md)