---
title: "Error del compilador CS0198 | Microsoft Docs"
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
  - "CS0198"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0198"
ms.assetid: 222c20f6-3f7f-4750-9f99-b5e6ae6c1271
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0198
Los campos del campo de solo lectura estático 'nombre' no se puede asignar \(excepto en un constructor estático o un inicializador de variables\)  
  
 Una variable [readonly](../Topic/readonly%20\(C%23%20Reference\).md) debe tener el mismo uso [estático](../Topic/static%20\(C%23%20Reference\).md) que el constructor en el que quiere inicializarla. Para obtener más información, consulta [Constructores estáticos](../Topic/Static%20Constructors%20\(C%23%20Programming%20Guide\).md).  
  
 El ejemplo siguiente genera la advertencia CS0198:  
  
```  
// CS0198.cs class MyClass { public static readonly int TestInt = 6; MyClass() { TestInt = 11;   // CS0198, constructor is not static and readonly field is } public static void Main() { } }  
```