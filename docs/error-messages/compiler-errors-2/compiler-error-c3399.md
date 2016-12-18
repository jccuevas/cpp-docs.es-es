---
title: "Error del compilador C3399 | Microsoft Docs"
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
  - "C3399"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3399"
ms.assetid: 306ad199-d150-4f6c-bcf1-24a7948b93be
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3399
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'tipo': no se pueden proporcionar argumentos cuando se crea una instancia de un parámetro genérico  
  
 Cuando se especifica la restricción `gcnew()`, se indica que el tipo de restricción tendrá un constructor sin parámetros. Por lo tanto, es un error tratar de crear una instancia de ese tipo y pasar un parámetro.  
  
 Vea [Restricciones de parámetros de tipo genérico \(C\+\+\/CLI\)](../Topic/Constraints%20on%20Generic%20Type%20Parameters%20\(C++-CLI\).md) para obtener más información.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C3399.  
  
```  
// C3399.cpp // compile with: /clr /c generic <class T> where T : gcnew() void f() { T t = gcnew T(1);   // C3399 T t2 = gcnew T();   // OK }  
```