---
title: "Error del compilador CS0026 | Microsoft Docs"
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
  - "CS0026"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0026"
ms.assetid: 8767fbc1-8ba7-4e88-a9f9-7e620411882b
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0026
La palabra clave 'this' no es válida en una propiedad, método o inicializador de campo estáticos  
  
 La palabra clave [this](../Topic/this%20\(C%23%20Reference\).md) hace referencia a un objeto, que es una instancia de un tipo. Puesto que los métodos estáticos son independientes de cualquier instancia de la clase contenedora, la palabra clave "this" no tiene sentido y, por tanto, no se permite. Para obtener más información, vea [Clases estáticas y sus miembros](../Topic/Static%20Classes%20and%20Static%20Class%20Members%20\(C%23%20Programming%20Guide\).md) y [Objetos](../Topic/Objects%20\(C%23%20Programming%20Guide\).md).  
  
## Ejemplo  
 El siguiente ejemplo genera el error CS0026:  
  
```  
// CS0026.cs public class A { public static int i = 0; public static void Main() { // CS0026 this.i = this.i + 1; // Try the following line instead: // i = i + 1; } }  
```