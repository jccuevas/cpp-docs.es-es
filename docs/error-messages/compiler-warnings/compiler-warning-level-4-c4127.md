---
title: "Advertencia del compilador (nivel 4) C4127 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4127"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4127"
ms.assetid: f59ded9e-5227-45bd-ac43-2aa861581363
caps.latest.revision: 12
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 4) C4127
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la expresión condicional es constante  
  
 La expresión de control de una instrucción `if` o un bucle `while` se evalúa como una constante. Si la expresión de control de un bucle `while` es una constante porque el bucle saldrá en el centro, considere reemplazar el bucle `while` por un bucle `for`. Puede omitir la inicialización, la prueba de terminación y el incremento de un bucle `for`, lo que provocará un bucle infinito \(como `while(1)`\) y puede salir del bucle desde el cuerpo de la instrucción `for`.  
  
 El ejemplo siguiente genera la advertencia C4127:  
  
```  
// C4127.cpp // compile with: /W4 #include <stdio.h> int main() { if (1 == 1) {}   // C4127 while (1) { break; }   // C4127 // OK for ( ; ; ) { printf("test\n"); break; } }  
```