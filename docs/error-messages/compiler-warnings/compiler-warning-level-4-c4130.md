---
title: "Advertencia del compilador (nivel 4) C4130 | Microsoft Docs"
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
  - "C4130"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4130"
ms.assetid: 45e4c7b2-6b51-41c7-ba5e-941aa5c7d3dc
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 4) C4130
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operador': operación lógica en dirección de una constante de cadena.  
  
 Usar el operador con la dirección de un literal de cadena produce código inesperado.  
  
 El ejemplo siguiente genera la advertencia C4130:  
  
```  
// C4130.cpp // compile with: /W4 int main() { char *pc; pc = "Hello"; if (pc == "Hello") // C4130 { } }  
```  
  
 La instrucción **if** compara el valor almacenado en el puntero `pc` con la dirección de la cadena "Hola", que se asigna por separado cada vez que aparece la cadena en el código. La instrucción **if** no compara la cadena a la que apunta `pc` con la cadena "Hola".  
  
 Para comparar cadenas, use la función `strcmp`.