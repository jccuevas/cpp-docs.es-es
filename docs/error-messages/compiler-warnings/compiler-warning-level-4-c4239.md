---
title: "Advertencia del compilador (nivel 4) C4239 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4239"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4239"
ms.assetid: a23dc16a-649e-4870-9a24-275de1584fcd
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Advertencia del compilador (nivel 4) C4239
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se ha utilizado una extensión no estándar : 'símbolo \(token\)' : conversión de 'tipo' a 'tipo'  
  
 Esta conversión de tipo no se permite en el estándar de C\+\+, pero sí aquí como extensión.  Esta advertencia siempre viene precedida de una explicación de al menos una línea que describe la regla del lenguaje que se ha infringido.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4239.  
  
```  
// C4239.cpp  
// compile with: /W4 /c  
struct C {  
   C() {}  
};  
  
void func(void) {  
   C & rC = C();   // C4239  
   const C & rC2 = C();   // OK  
   rC2;  
}  
```  
  
## Ejemplo  
 No se permite estrictamente la conversión de un tipo entero a un tipo enum.  
  
 El ejemplo siguiente genera el error C4239.  
  
```  
// C4239b.cpp  
// compile with: /W4 /c  
enum E { value };   
struct S {   
   E e : 2;   
} s = { 5 };   // C4239   
// try the following line instead  
// } s = { (E)5 };  
```