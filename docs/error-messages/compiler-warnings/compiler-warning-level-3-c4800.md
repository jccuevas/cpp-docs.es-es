---
title: "Advertencia del compilador (nivel 3) C4800 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4800"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4800"
ms.assetid: 4f409799-a250-45ed-bb5f-657691b0d9f7
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Advertencia del compilador (nivel 3) C4800
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'tipo' : forzando el valor a bool 'true' o 'false' \(advertencia de rendimiento\)  
  
 Esta advertencia se genera cuando a un valor distinto de `bool` se asigna o fuerza su conversión al tipo `bool`.  Normalmente, este mensaje lo origina la asignación de variables `int` a variables `bool` en casos en los que la variable `int` sólo contiene valores **true** y **false**, y puede volver a declararse como un tipo `bool`.  Si no se puede volver a escribir la expresión para que utilice el tipo `bool`, se puede agregar "`!=0`" a la expresión, lo que le asigna el tipo `bool`.  Convertir la expresión al tipo `bool` no deshabilita la advertencia, que forma parte del diseño del compilador.  
  
 El código siguiente genera el error C4800:  
  
```  
// C4800.cpp  
// compile with: /W3  
int main() {  
   int i = 0;  
  
   // try..  
   // bool i = 0;  
  
   bool j = i;   // C4800  
   j++;  
}  
```