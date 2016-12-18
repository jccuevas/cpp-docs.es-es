---
title: "Error del compilador C2537 | Microsoft Docs"
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
  - "C2537"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2537"
ms.assetid: aee81d8e-300e-4a8b-b6c4-b3828398b34e
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2537
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'especificador' : especificación de vinculación no válida  
  
 Causas posibles:  
  
1.  No se admite el especificador de vinculación.  Sólo se admite el especificador de vinculación "C".  
  
2.  La vinculación "C" se especifica para más de una función en un conjunto de funciones sobrecargadas.  Esto no está permitido.  
  
 El código siguiente genera el error C2537:  
  
```  
// C2537.cpp  
// compile with: /c  
extern "c" void func();   // C2537  
extern "C" void func2();   // OK  
```