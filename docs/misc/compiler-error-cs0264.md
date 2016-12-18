---
title: "Error del compilador CS0264 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0264"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0264"
ms.assetid: a8a87185-5915-4b0d-a8cd-2f129ea51b8f
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0264
Las declaraciones parciales de 'type' deben tener los mismos nombres de parámetros de tipo en el mismo orden  
  
 Este error se produce si se está definiendo un tipo genérico en declaraciones parciales y los parámetros de tipo no son coherentes en el nombre u orden en todas las declaraciones parciales. Para evitar este error, compruebe los parámetros de tipo de cada declaración parcial y asegúrese de que se usa el mismo nombre y orden de los parámetros. Para más información, vea [Clases y métodos parciales](../Topic/Partial%20Classes%20and%20Methods%20\(C%23%20Programming%20Guide\).md) y [Parámetros de tipos genéricos](../Topic/Generic%20Type%20Parameters%20\(C%23%20Programming%20Guide\).md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS0264:  
  
```  
// CS0264.cs partial class MyClass<T>  // CS0264 { } partial class MyClass <MyType> { }  
```