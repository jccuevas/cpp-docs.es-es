---
title: "Error del compilador CS0753 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0753"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0753"
ms.assetid: 287dd9da-da74-4290-9fa1-21ef1a8150fe
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0753
Solo los métodos, las clases, las estructuras o las interfaces pueden ser parciales.  
  
 El modificador [parcial](../Topic/partial%20\(Type\)%20\(C%23%20Reference\).md) solo puede usarse con clases, estructuras, interfaces y métodos.  
  
### Para corregir este error  
  
1.  Quite el modificador `partial` de la construcción de idioma o variable.  
  
## Ejemplo  
 El código siguiente genera el error CS0753:  
  
```  
// cs0753.cs using System; public partial class C { partial int num; // CS0753 public static int Main() { return 1; } }  
```  
  
## Vea también  
 [Clases y métodos parciales](../Topic/Partial%20Classes%20and%20Methods%20\(C%23%20Programming%20Guide\).md)