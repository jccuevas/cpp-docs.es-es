---
title: "Advertencia del compilador (nivel 4) CS0028 | Microsoft Docs"
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
  - "CS0028"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0028"
ms.assetid: 47df919f-01fa-45ae-a4b7-912445e679e2
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 4) CS0028
'declaración de función' tiene la signatura incorrecta para ser un punto de entrada.  
  
 La declaración de método para `Main` no es válida: se ha declarado con una signatura no válida.`Main` debe declararse como static y debe devolver [int](../Topic/int%20\(C%23%20Reference\).md) o [void](../Topic/void%20\(C%23%20Reference\).md). Para obtener más información, consulta [Main\(\) y argumentos de la línea de comandos](../Topic/Main\(\)%20and%20Command-Line%20Arguments%20\(C%23%20Programming%20Guide\).md).  
  
 El ejemplo siguiente genera la advertencia CS0028:  
  
```  
// CS0028.cs // compile with: /W:4 /warnaserror public class a { public static double Main(int i)   // CS0028 // Try the following line instead: // public static void Main() { } }  
```