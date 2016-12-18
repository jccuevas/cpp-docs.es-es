---
title: "Advertencia del compilador (nivel 2) C4396 | Microsoft Docs"
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
  - "C4396"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4396"
ms.assetid: 7cd6b283-db17-4574-b299-03e0b913ad70
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 2) C4396
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

"name": el especificador inline no se puede usar cuando una declaración de confianza hace referencia a una especialización de una plantilla de función  
  
 Una especialización de una plantilla de función no puede especificar ninguno de los especificadores [inline](../../misc/inline-inline-forceinline.md). El compilador emite la advertencia C4396 y omite el especificador inline.  
  
### Para corregir este error  
  
-   Quite el especificador `inline`, `__inline` o `__forceinline` de la declaración de función friend.  
  
## Ejemplo  
 El ejemplo de código siguiente muestra una declaración de función friend no válida con un especificador `inline`.  
  
```  
// C4396.cpp // compile with: /W2 /c class X; template<class T> void Func(T t, int i); class X { friend inline void Func<char>(char t, int i);  //C4396 // try the following line instead //    friend void Func<char>(char t, int i); int i; };  
```