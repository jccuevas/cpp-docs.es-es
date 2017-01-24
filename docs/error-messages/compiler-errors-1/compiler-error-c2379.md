---
title: "Error del compilador C2379 | Microsoft Docs"
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
  - "C2379"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2379"
ms.assetid: 37dc3015-a4af-4341-bbf3-da6150df7e51
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2379
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

el parámetro formal número tiene un tipo diferente tras la promoción  
  
 El tipo del parámetro especificado no es compatible mediante promociones predeterminadas con el tipo de una declaración anterior.  Se trata de un error en ANSI C \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\) y de una advertencia en las extensiones de Microsoft \(**\/Ze**\).  
  
 El código siguiente genera el error C2379:  
  
```  
// C2379.c  
// compile with: /Za  
void func();  
void func(char);   // C2379, char promotes to int  
```