---
title: "Error del compilador CS0180 | Microsoft Docs"
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
  - "CS0180"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0180"
ms.assetid: a21bf0a2-ed5a-4ddd-88d3-240babc5888a
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0180
'member' no puede ser a la vez extern y abstract  
  
 Las palabras clave [abstract](../Topic/abstract%20\(C%23%20Reference\).md) y [extern](../Topic/extern%20\(C%23%20Reference\).md) son mutuamente excluyentes. La palabra clave `extern` implica que el miembro está definido fuera del archivo; **abstract** implica que la implementación se ofrece en una clase derivada. Para obtener más información, consulta [Métodos](../Topic/Methods%20\(C%23%20Programming%20Guide\).md).  
  
 El ejemplo siguiente genera la advertencia CS0180:  
  
```  
// CS0180.cs namespace MyNamespace { public class MyClass { public extern abstract int Foo(int a);   // CS0180 public static void Main() { } } }  
```