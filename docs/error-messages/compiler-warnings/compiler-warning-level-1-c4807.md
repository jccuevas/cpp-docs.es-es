---
title: "Advertencia del compilador (nivel 1) C4807 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4807"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4807"
ms.assetid: 089c9f87-fd81-402e-9826-66a8ef1ef1fe
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Advertencia del compilador (nivel 1) C4807
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operation': combinación no segura del tipo 'type' y el campo de bits con signo de tipo 'type'  
  
 Esta advertencia se genera al comparar un campo de bits con signo de un bit con una variable `bool`. Puesto que el campo de bits con signo de un bit solo puede contener los valores \-1 o 0, es arriesgado compararlo con `bool`. No se generan advertencias con la mezcla de `bool` y campos de bits sin signo de un bit, ya que son idénticas a `bool` y solo pueden contener 0 o 1.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C4807:  
  
```  
// C4807.cpp // compile with: /W1 typedef struct bitfield { signed mybit : 1; } mybitfield; int main() { mybitfield bf; bool b = true; // try.. // int b = true; bf.mybit = -1; if (b == bf.mybit) {   // C4807 b = false; } }  
```