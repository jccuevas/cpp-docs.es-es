---
title: "Error del compilador CS0192 | Microsoft Docs"
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
  - "CS0192"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0192"
ms.assetid: d3fb6d18-dbf3-42c3-a280-afe55b97c2d1
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0192
Los campos del campo de solo lectura estático 'name' no se pueden pasar como out ni ref \(excepto en un constructor estático\)  
  
 Un campo \(variable\) marcado con la palabra clave [readonly](../Topic/readonly%20\(C%23%20Reference\).md) no se puede pasar a un parámetro [ref](../Topic/ref%20\(C%23%20Reference\).md) o [out](../Topic/out%20\(C%23%20Reference\).md) excepto dentro de un constructor. Para obtener más información, consulta [Campos](../Topic/Fields%20\(C%23%20Programming%20Guide\).md).  
  
 CS0192 también se produce si el campo `readonly` es [static](../Topic/static%20\(C%23%20Reference\).md) y el constructor no está marcado como `static`.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0192:  
  
```  
// CS0192.cs class MyClass { public readonly int TestInt = 6; static void TestMethod(ref int testInt) { testInt = 0; } MyClass() { TestMethod(ref TestInt);   // OK } public void PassReadOnlyRef() { TestMethod(ref TestInt);   // CS0192 } public static void Main() { } }  
```