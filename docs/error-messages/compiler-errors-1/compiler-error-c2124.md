---
title: "Error del compilador C2124 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2124"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2124"
ms.assetid: 93392aaa-5582-4d68-8cc5-bd9c62a0ae7e
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C2124
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

división \(normal o módulo\) por cero  
  
 Una expresión constante incluye un denominador cero. Para resolver el error, no divida por cero.  
  
 El ejemplo siguiente genera la advertencia C2124:  
  
```  
// C2124.cpp int main() { int i = 1 / 0;   // C2124  do not divide by zero int i2 = 12 / 2;   // OK }  
```