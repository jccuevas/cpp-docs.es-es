---
title: "Se usaron operandos de tipo Object para el operador &#39;&lt;s&#237;mboloDeOperador&gt;&#39;; podr&#237;an producirse errores en tiempo de ejecuci&#243;n | Microsoft Docs"
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
  - "BC42019"
  - "vbc42019"
helpviewer_keywords: 
  - "BC42019"
ms.assetid: f61944ba-863b-4a82-aae4-249bda52ec8d
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Se usaron operandos de tipo Object para el operador &#39;&lt;s&#237;mboloDeOperador&gt;&#39;; podr&#237;an producirse errores en tiempo de ejecuci&#243;n
Una expresión usa un operador para el que uno o ambos operandos son del [Object \(Tipo de datos\)](../Topic/Object%20Data%20Type.md).  
  
 Si una variable o expresión se evalúa como `Object`, el compilador debe realizar el *enlace en tiempo de ejecución*, que produce operaciones adicionales en tiempo de ejecución. También expone la aplicación a posibles errores en tiempo de ejecución. Por ejemplo, suponga que asigna un <xref:System.Windows.Forms.Form> a una variable `Object` e intenta usarlo con [\/ \(Operador\)](../Topic/-%20Operator%20\(Visual%20Basic\)3.md). Si lo hace, el tiempo de ejecución inicia una <xref:System.InvalidCastException> porque Visual Basic no puede convertir un objeto <xref:System.Windows.Forms.Form> en un valor numérico.  
  
 De forma predeterminada, este mensaje es una advertencia. Para obtener información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../Topic/Configuring%20Warnings%20in%20Visual%20Basic.md).  
  
 **Identificador de error:** BC42019  
  
### Para corregir este error  
  
-   Si es posible, organice los operandos para evaluarlos como los tipos de datos para los que está definido el operador.  
  
## Vea también  
 [Operadores aritméticos en Visual Basic](../Topic/Arithmetic%20Operators%20in%20Visual%20Basic.md)