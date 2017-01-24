---
title: "Error del compilador CS0255 | Microsoft Docs"
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
  - "CS0255"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0255"
ms.assetid: b45f5d5a-1923-4fe1-a858-e5ef5590a108
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0255
stackalloc no se puede usar en un bloque catch o finally  
  
 La palabra clave [stackalloc](../Topic/stackalloc%20\(C%23%20Reference\).md) no se puede usar en un bloque [catch](../Topic/try-catch%20\(C%23%20Reference\).md) o [finally](../Topic/try-catch-finally%20\(C%23%20Reference\).md). Para obtener más información, consulta [Excepciones y control de excepciones](../Topic/Exceptions%20and%20Exception%20Handling%20\(C%23%20Programming%20Guide\).md).  
  
 El ejemplo siguiente genera la advertencia CS0255:  
  
```  
// CS0255.cs // compile with: /unsafe using System; public class TestTryFinally { public static unsafe void Test() { int i = 123; string s = "Some string"; object o = s; try { // Conversion is not valid; o contains a string not an int i = (int) o; } finally { Console.Write("i = {0}", i); int* fib = stackalloc int[100];   // CS0255 } } public static void Main() { } }  
```