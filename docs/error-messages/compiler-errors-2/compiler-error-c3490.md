---
title: "Error del compilador C3490 | Microsoft Docs"
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
  - "C3490"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3490"
ms.assetid: 7638559a-fd06-4527-a9c1-0c8ae68b3123
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3490
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var' no se puede modificar porque se está accediendo a través de un objeto const.  
  
 Una expresión lambda que se declara en un método `const` no puede modificar los datos de miembro no mutable.  
  
### Para corregir este error  
  
-   Elimine el modificador `const` de la declaración del método.  
  
## Ejemplo  
 El ejemplo siguiente genera C3490 porque modifica la variable miembro `_i` en un método `const`:  
  
```  
// C3490a.cpp // compile with: /c class C { void f() const  { auto x = [=]() { _i = 20; }; // C3490 } int _i; };  
```  
  
## Ejemplo  
 En el ejemplo siguiente se resuelve C3490 quitando el modificador `const` de la declaración del método:  
  
```  
// C3490b.cpp // compile with: /c class C { void f() { auto x = [=]() { _i = 20; }; } int _i; };  
```  
  
## Vea también  
 [Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)