---
title: "Advertencia del compilador (nivel 4) C4918 | Microsoft Docs"
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
  - "C4918"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4918"
ms.assetid: 1bcf6d35-3467-4aa8-b2ef-cb33f4e70238
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 4) C4918
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'character': carácter no válido en la lista de optimizaciones de pragma  
  
 Se encontró un carácter desconocido en la lista de optimizaciones de una instrucción pragma [optimize](../../preprocessor/optimize.md).  
  
 Por ejemplo, la siguiente instrucción genera la advertencia C4918:  
  
```  
// C4918.cpp // compile with: /W4 #pragma optimize("X", on) // C4918 expected int main() { }  
```