---
title: "Error del compilador CS0761 | Microsoft Docs"
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
  - "CS0761"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0761"
ms.assetid: b16ac1df-0ddc-44d2-89f1-8d9c32af87ad
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0761
Las declaraciones de métodos parciales de 'método\<T\>' tienen restricciones de parámetros de tipo incoherentes.  
  
 Si un método parcial tiene una implementación, la restricción de tipo genérico debe ser idéntica a la restricción definida en la signatura del método.  
  
### Para corregir este error  
  
1.  Haga que las restricciones de tipo genérico sean idénticas en cada parte del método parcial.  
  
## Ejemplo  
 El código siguiente genera el error CS0761:  
  
```  
// cs0761.cs using System; public partial class C { partial void Part<T>() where T : class; partial void Part<T>() where T : struct // CS0761 { } public static int Main() { return 1; } }  
  
```  
  
## Vea también  
 [Clases y métodos parciales](../Topic/Partial%20Classes%20and%20Methods%20\(C%23%20Programming%20Guide\).md)   
 [Restricciones de tipos de parámetros](../Topic/Constraints%20on%20Type%20Parameters%20\(C%23%20Programming%20Guide\).md)