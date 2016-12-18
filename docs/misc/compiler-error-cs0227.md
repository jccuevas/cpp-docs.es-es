---
title: "Error del compilador CS0227 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0227"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0227"
ms.assetid: b595a1c9-8204-4ff7-a1d0-258b0b1d6ff7
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0227
El código no seguro solo puede aparecer si se compila con \/unsafe  
  
 Si el código fuente contiene la palabra clave [unsafe](../Topic/unsafe%20\(C%23%20Reference\).md), también debe usarse la opción del compilador [\/ unsafe](../Topic/-unsafe%20\(C%23%20Compiler%20Options\).md). Para obtener más información, consulta [Código no seguro y punteros](../Topic/Unsafe%20Code%20and%20Pointers%20\(C%23%20Programming%20Guide\).md).  
  
 Para establecer la opción no segura en [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)], haga clic en **Proyecto** en el menú principal, seleccione el panel **Compilar** y active la casilla que indica "permitir código no seguro".  
  
 El ejemplo siguiente, cuando se compila sin **\/unsafe**, genera el error CS0227:  
  
```  
// CS0227.cs public class MyClass { unsafe public static void Main()   // CS0227 { } }  
```  
  
## Vea también  
 [C\# Compiler Errors](../Topic/C%23%20Compiler%20Errors.md)