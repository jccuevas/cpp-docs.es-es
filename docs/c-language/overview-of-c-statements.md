---
title: "Informaci&#243;n general sobre las instrucciones de C | Microsoft Docs"
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
  - "punto y coma"
  - "punto y coma, en instrucciones de C"
  - "instrucciones, acerca de las instrucciones"
  - "instrucciones, C"
  - "Visual C, instrucciones"
ms.assetid: 0d49837a-5399-4881-b60c-af5f4e9720de
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Informaci&#243;n general sobre las instrucciones de C
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las instrucciones de C se componen de tokens, expresiones y otras instrucciones.  Una instrucción que forma un componente de otra instrucción se denomina el “cuerpo” de la instrucción de inclusión.  En esta sección se analiza cada tipo de instrucción que se da con la sintaxis siguiente.  
  
## Sintaxis  
 *statement*:  
 [labeled\-statement](../c-language/goto-and-labeled-statements-c.md)  
  
 [compound\-statement](../c-language/compound-statement-c.md)  
  
 [expression\-statement](../c-language/expression-statement-c.md)  
  
 [selection\-statement](../c-language/if-statement-c.md)  
  
 [iteration\-statement](../c-language/do-while-statement-c.md)  
  
 [jump\-statement](../c-language/break-statement-c.md)  
  
 [try\-except\-statement](../c-language/try-except-statement-c.md)  
  
 \/\* Específico de Microsoft \*\/[instrucción try\-finally](../c-language/try-finally-statement-c.md) \/\* Específico de Microsoft \*\/  
  
 Con frecuencia, el cuerpo de la instrucción es una "instrucción compuesta". Una instrucción compuesta consta de otras instrucciones que pueden incluir palabras clave.  La instrucción compuesta está delimitada por llaves \(**{ }**\).  El resto de las instrucciones de C finalizan con un punto y coma \(**;**\).  El punto y coma es un terminador de instrucciones.  
  
 La instrucción de expresión contiene una expresión de C que puede contener los operadores aritméticos o lógicos que se presentan en [Expresiones y asignaciones](../c-language/expressions-and-assignments.md).  La instrucción nula es una instrucción vacía.  
  
 Cualquier instrucción de C puede empezar con una etiqueta identificativa que consta de un nombre y dos puntos.  Como solo la instrucción `goto` reconoce etiquetas de instrucciones, las etiquetas de instrucciones se tratan con `goto`.  Vea [Instrucciones goto y con etiquetas](../c-language/goto-and-labeled-statements-c.md) para obtener más información.  
  
## Vea también  
 [Instrucciones](../c-language/statements-c.md)