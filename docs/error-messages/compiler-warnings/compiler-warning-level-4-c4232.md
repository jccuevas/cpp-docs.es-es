---
title: "Advertencia del compilador (nivel 4) C4232 | Microsoft Docs"
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
  - "C4232"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4232"
ms.assetid: f92028a5-4ddd-43c1-97f5-4f724e5e14af
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 4) C4232
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se ha utilizado una extensión no estándar : 'identificador' : la dirección de dllimport 'dllimport' no es estática, no se garantiza la identidad  
  
 Con las extensiones de Microsoft habilitadas \(\/Ze\), se puede indicar un valor no estático como dirección de una función declarada mediante el modificador **dllimport**.  Cuando está habilitada la compatibilidad con ANSI \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\), esto puede causar un error.  
  
 El código siguiente genera el error C4232:  
  
```  
// C4232.c  
// compile with: /W4 /Ze /c  
int __declspec(dllimport) f();  
int (*pfunc)() = &f;   // C4232  
```