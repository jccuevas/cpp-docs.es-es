---
title: "System.Diagnostics.DebuggerHiddenAttribute no afecta a &#39;Get&#39; o &#39;Set&#39; cuando se aplica a la definici&#243;n de propiedad | Microsoft Docs"
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
  - "bc40051"
  - "vbc40051"
helpviewer_keywords: 
  - "BC40051"
ms.assetid: 623d5e48-7fb2-48a9-bbbb-92914b08c01c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# System.Diagnostics.DebuggerHiddenAttribute no afecta a &#39;Get&#39; o &#39;Set&#39; cuando se aplica a la definici&#243;n de propiedad
System.Diagnostics.DebuggerHiddenAttribute no afecta a 'Get' o 'Set' cuando se aplica a la definición de propiedad. Aplique directamente el atributo a los procedimientos 'Get' y 'Set' según corresponda.  
  
 El atributo <xref:System.Diagnostics.DebuggerHiddenAttribute> se aplica a una declaración de propiedad.  
  
 El código fuente puede aplicar el atributo <xref:System.Diagnostics.DebuggerHiddenAttribute> a un procedimiento. De esa manera se indica al depurador de Visual Studio que no se detenga dentro del procedimiento y que no permita que se establezcan puntos de interrupción en el procedimiento.  
  
 Aunque puede aplicar <xref:System.Diagnostics.DebuggerHiddenAttribute> a una propiedad, no surte efecto. Solo tiene el efecto deseado si lo aplica al procedimiento `Get` o `Set` de la propiedad.  
  
 De forma predeterminada, este mensaje es una advertencia. Para más información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md).  
  
 **Identificador de error:** BC40051  
  
### Para corregir este error  
  
-   Quite el atributo <xref:System.Diagnostics.DebuggerHiddenAttribute> de la declaración de propiedad y aplíquelo al procedimiento `Get` o `Set` de la propiedad según corresponda.  
  
## Vea también  
 <xref:System.Diagnostics.DebuggerHiddenAttribute>   
 [Procedimientos de propiedad](../Topic/Property%20Procedures%20\(Visual%20Basic\).md)   
 [Property \(Instrucción\)](../Topic/Property%20Statement.md)   
 [Get \(Instrucción\)](../Topic/Get%20Statement.md)   
 [Set \(Instrucción\)](../Topic/Set%20Statement%20\(Visual%20Basic\).md)