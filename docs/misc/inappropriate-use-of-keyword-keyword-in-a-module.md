---
title: "Uso no apropiado de la palabra clave &lt;keyword&gt; en un m&#243;dulo | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42028"
  - "BC42028"
helpviewer_keywords: 
  - "BC42028"
ms.assetid: a9bc1e9d-ba2c-4a71-b147-0fb66f670316
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Uso no apropiado de la palabra clave &lt;keyword&gt; en un m&#243;dulo
Los módulos no tienen instancias, no admiten la herencia ni implementan interfaces. Por lo tanto, las palabras clave siguientes no se aplican a una declaración de módulo:  
  
-   [MustInherit](../Topic/MustInherit%20\(Visual%20Basic\).md)  
  
-   [NotInheritable](../Topic/NotInheritable%20\(Visual%20Basic\).md)  
  
-   [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md)  
  
-   [Private](../Topic/Private%20\(Visual%20Basic\).md)  
  
-   [Protected](../Topic/Protected%20\(Visual%20Basic\).md)  
  
-   [Shadows](../Topic/Shadows%20\(Visual%20Basic\).md)  
  
-   [Shared](../Topic/Shared%20\(Visual%20Basic\).md)  
  
-   [Static](../Topic/Static%20\(Visual%20Basic\).md)  
  
 Las únicas palabras clave que se admiten en una [Module \(Instrucción\)](../Topic/Module%20Statement.md) son [Public](../Topic/Public%20\(Visual%20Basic\).md) y [Friend](../Topic/Friend%20\(Visual%20Basic\).md).  
  
 Además, no puede usar la instrucción [Implements](../Topic/Implements%20Clause%20\(Visual%20Basic\).md) o la [Inherits \(Instrucción\)](../Topic/Inherits%20Statement.md) en el bloque de instrucciones del módulo.  
  
 De forma predeterminada, este mensaje es una advertencia. Para más información sobre cómo ocultar las advertencias o tratarlas como errores, vea [Configurar advertencias en Visual Basic](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md).  
  
 **Identificador de error:** BC42028  
  
### Para corregir este error  
  
-   Si desea que este elemento de programación sea un módulo, use solo la palabra clave `Public` o `Friend` en su declaración. De forma predeterminada, un módulo se usa para `Friend` si no se especifica su nivel de acceso.  
  
-   Si piensa crear instancias de este elemento de programación, declárelo como una clase. A continuación, podrá usar las palabras clave que se aplican a una declaración de clase.  
  
## Vea también  
 [Class \(Instrucción\)](../Topic/Class%20Statement%20\(Visual%20Basic\).md)