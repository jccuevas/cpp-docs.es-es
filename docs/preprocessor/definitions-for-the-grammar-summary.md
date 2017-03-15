---
title: "Definiciones del resumen de la gram&#225;tica | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "preprocesador"
  - "preprocesador, definiciones"
ms.assetid: cc752dc8-6f4e-4347-a556-e0d9ef4c46bd
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Definiciones del resumen de la gram&#225;tica
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los elementos terminales son extremos en una definición de sintaxis.  No hay ninguna otra posible resolución.  Los elementos terminales incluyen el conjunto de palabras reservadas e identificadores definidos por el usuario.  
  
 Los elementos no terminales son marcadores en la sintaxis.  La mayoría se definen en otro lugar en este resumen de la sintaxis.  Las definiciones pueden ser recursivas.  Los siguientes elementos no terminales se definen en el [Resumen de la gramática](../misc/grammar-summary-cpp.md) de la *Referencia del lenguaje C\+\+*:  
  
 `constant`, *constant\-expression*, *identifier*, *keyword*, `operator`, `punctuator`  
  
 Un componente opcional se indica mediante el subíndice opt.  Por ejemplo, lo siguiente indica una expresión opcional delimitada por llaves:  
  
 **{** *expresión*opt **}**  
  
## Vea también  
 [Resumen de la gramática](../preprocessor/grammar-summary-c-cpp.md)