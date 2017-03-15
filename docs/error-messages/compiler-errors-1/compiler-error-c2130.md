---
title: "Error del compilador C2130 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2130"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2130"
ms.assetid: c6fd5a7e-8f28-4f67-99d1-95a13b0dff90
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Error del compilador C2130
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#line esperaba una cadena con el nombre de archivo, pero se encontró 'token'  
  
 El token de nombre de archivo opcional que se encuentra después de [\#line](../../preprocessor/hash-line-directive-c-cpp.md) `linenumber` debe ser una cadena.  
  
 El ejemplo siguiente genera la advertencia C2130:  
  
```  
// C2130.cpp int main() { #line 1000 test   // C2130 #line 1000 "test"   // OK }  
```