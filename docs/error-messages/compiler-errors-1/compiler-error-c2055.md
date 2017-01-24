---
title: "Error del compilador C2055 | Microsoft Docs"
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
  - "C2055"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2055"
ms.assetid: 6cec79cc-6bec-443f-9897-fbf5452718c7
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2055
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se esperaba una lista de parámetros formales, no una lista de tipos  
  
 La definición de una función contiene un lista de tipos de parámetros en vez de una lista de parámetros formales.  ANSI C requiere que los parámetros formales tengan un nombre, a menos que sean de tipo void o de puntos suspensivos \(`...`\).  
  
 El código siguiente genera el error C2055:  
  
```  
// C2055.c  
// compile with: /c  
void func(int, char) {}  // C2055  
void func (int i, char c) {}   // OK  
```