---
title: "&lt;tipo1&gt; &#39;&lt;nombreDeMiembro&gt;&#39; ensombrece un miembro sobrecargable declarado en el tipo base &lt;tipo2&gt; &#39;&lt;nombreDeClase&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc40003"
  - "vbc40003"
helpviewer_keywords: 
  - "BC40003"
ms.assetid: 1e0d2061-0ad9-4915-b946-d55cb5d5ee80
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;tipo1&gt; &#39;&lt;nombreDeMiembro&gt;&#39; ensombrece un miembro sobrecargable declarado en el tipo base &lt;tipo2&gt; &#39;&lt;nombreDeClase&gt;&#39;
\<tipo1\> '\<nombreDeMiembro\>' ensombrece un miembro sobrecargable declarado en el tipo base \<tipo2\> '\<nombreDeClase\>'. Si quiere sobrecargar el método base, este método se debe declarar 'Overloads'.  
  
 Una clase derivada define un procedimiento `Function` o `Sub` o una `Property` con el mismo nombre que un procedimiento o una propiedad definido en la clase base. Dado que los procedimientos y las propiedades son miembros sobrecargables, la clase derivada puede sobrecargar o sombrear el miembro de clase base. Sin embargo, el código de la clase derivada no especifica [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md) ni [Shadows](../Topic/Shadows%20\(Visual%20Basic\).md) en la declaración. En ausencia de una palabra clave, el compilador supone `Shadows`.  
  
 Se recomienda especificar `Overloads` o `Shadows`. Ello facilita la lectura y la comprensión del código.  
  
 De forma predeterminada, este mensaje es una advertencia. Para más información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md).  
  
 **Identificador de error:** BC40003  
  
### Para corregir este error  
  
-   Si desea sobrecargar la propiedad o el método de clase base, incluya la palabra clave `Overloads` en la declaración.  
  
-   Si desea ensombrecer la propiedad o el método de clase base, incluya la palabra clave `Shadows` en lugar de `Overloads`.  
  
-   Si no desea sobrecargar ni sombrear al miembro de clase base, cambie el nombre del miembro de la clase derivada.  
  
## Vea también  
 [Sobrecarga de procedimientos](../Topic/Procedure%20Overloading%20\(Visual%20Basic\).md)   
 [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md)   
 [Shadows](../Topic/Shadows%20\(Visual%20Basic\).md)   
 [Sombrear en Visual Basic](../Topic/Shadowing%20in%20Visual%20Basic.md)   
 [Function \(Instrucción\)](../Topic/Function%20Statement%20\(Visual%20Basic\).md)   
 [Sub \(Instrucción\)](../Topic/Sub%20Statement%20\(Visual%20Basic\).md)   
 [Property \(Instrucción\)](../Topic/Property%20Statement.md)