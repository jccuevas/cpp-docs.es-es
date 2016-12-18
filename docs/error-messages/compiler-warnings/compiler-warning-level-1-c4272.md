---
title: "Advertencia del compilador (nivel 1) C4272 | Microsoft Docs"
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
  - "C4272"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4272"
ms.assetid: 0d6c1de4-2eef-42c4-b861-c221f8b495ef
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4272
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : está marcada con \_\_declspec \(dllimport\); debe especificar la convención de llamadas nativa al importar una función.  
  
 Es un error exportar una función marcada con la convención de llamadas [\_\_clrcall](../../cpp/clrcall.md); el compilador emite esta advertencia si se intenta importar una función marcada con `__clrcall`.  
  
 El código siguiente genera el error C4272:  
  
```  
// C4272.cpp  
// compile with: /c /W1 /clr  
__declspec(dllimport) void __clrcall Test();   // C4272  
__declspec(dllimport) void Test2();   // OK  
```