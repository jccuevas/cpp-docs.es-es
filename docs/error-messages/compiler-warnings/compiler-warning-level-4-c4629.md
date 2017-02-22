---
title: "Advertencia del compilador (nivel 4) C4629 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4629"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4629"
ms.assetid: 158cde12-bae5-4d43-b575-b52b35aaa0b9
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Advertencia del compilador (nivel 4) C4629
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Dígrafo usado, secuencia de caracteres 'dígrafo' interpretada como token 'char' \(inserte un espacio entre los dos caracteres si no es lo que tenía previsto\)  
  
 En [\/Za](../../build/reference/za-ze-disable-language-extensions.md), el compilador le advierte cuando detecta un dígrafo.  
  
 El ejemplo siguiente genera la advertencia C4629:  
  
```  
// C4629.cpp // compile with: /Za /W4 int main() <%   // C4629 <% digraph for { }  
```