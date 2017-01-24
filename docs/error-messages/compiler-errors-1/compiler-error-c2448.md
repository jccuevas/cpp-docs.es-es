---
title: "Error del compilador C2448 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2448"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2448"
ms.assetid: e255df3c-f861-4b4d-a193-8768cef061a5
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2448
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador' : el inicializador de estilo de función parece ser una definición de función  
  
 La definición de función es incorrecta.  
  
 Este error puede deberse a una lista formal del lenguaje C de estilo antiguo.  
  
 El código siguiente genera el error C2448:  
  
```  
// C2448.cpp  
void func(c)  
   int c;  
{}   // C2448  
```