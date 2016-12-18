---
title: "Error del compilador CS0061 | Microsoft Docs"
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
  - "CS0061"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0061"
ms.assetid: 8dfc57a9-653d-4902-a88c-92032ba64024
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0061
Incoherencia de accesibilidad: la interfaz base 'interfaz 1' es menos accesible que la interfaz 'interfaz 2'.  
  
 Una construcción [public](../Topic/public%20\(C%23%20Reference\).md) debe devolver un objeto accesible públicamente.  
  
 No se puede restringir la accesibilidad de la interfaz en una interfaz derivada. Para obtener más información, vea [Interfaces](../Topic/Interfaces%20\(C%23%20Programming%20Guide\).md) y [Modificadores de acceso](../Topic/Access%20Modifiers%20\(C%23%20Programming%20Guide\).md).  
  
 El ejemplo siguiente genera la advertencia CS0061.  
  
```  
// CS0061.cs // compile with: /target:library internal interface A {} public interface AA : A {}  // CS0061 // OK public interface B {} internal interface BB : B {} internal interface C {} internal interface CC : C {}  
```