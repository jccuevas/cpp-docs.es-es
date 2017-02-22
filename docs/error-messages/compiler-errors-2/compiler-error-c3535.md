---
title: "Error del compilador C3535 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3535"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3535"
ms.assetid: 24449c98-f681-484d-a00b-32533dca3a88
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error del compilador C3535
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se puede deducir el tipo para "tipo1" de "tipo2"  
  
 El tipo de variable declarada por la palabra clave `auto` no se puede deducir del tipo de expresión de inicialización.  Por ejemplo, este error se produce si la expresión de inicialización se evalúa como `void`, que no es un tipo.  
  
### Para corregir este error  
  
1.  Asegúrese de que el tipo de expresión de inicialización no es `void`.  
  
2.  Asegúrese de que la declaración no es un puntero a un tipo fundamental.  Para obtener más información, vea [Tipos fundamentales](../../cpp/fundamental-types-cpp.md).  
  
3.  Asegúrese de que, si la declaración es un puntero a un tipo, la expresión de inicialización sea un tipo de puntero.  
  
## Ejemplo  
 En el ejemplo siguiente se genera el error C3535 porque la expresión de inicialización se evalúa como `void`.  
  
```  
// C3535a.cpp  
// Compile with /Zc:auto  
void f(){}  
int main()  
{  
   auto x = f();   //C3535  
   return 0;  
}  
```  
  
## Ejemplo  
 En el ejemplo siguiente se genera el error C3535 porque la instrucción declara la variable `x` como puntero a un tipo deducido, pero el tipo de la expresión de inicializador es doble.  Por consiguiente, el compilador no puede deducir el tipo de la variable.  
  
```  
// C3535b.cpp  
// Compile with /Zc:auto  
int main()  
{  
   auto* x = 123.0;   // C3535  
   return 0;  
}  
```  
  
## Ejemplo  
 En el ejemplo siguiente se genera el error C3535 porque la variable `p` declara un puntero a un tipo deducido, pero la expresión de inicialización no es un tipo de puntero.  
  
```  
// C3535c.cpp  
// Compile with /Zc:auto  
class A { };  
A x;  
auto *p = x;  // C3535  
```  
  
## Vea también  
 [auto \(Palabra clave\)](../../cpp/auto-keyword.md)   
 [Tipos fundamentales](../../cpp/fundamental-types-cpp.md)