---
title: "Identificadores en expresiones primarias | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "identificadores, designar objetos"
ms.assetid: d4602fe6-e7e6-40cc-9823-3b1ebf5d3d38
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Identificadores en expresiones primarias
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los identificadores pueden ser de tipo entero, **float**, `enum`, `struct`, **union**, matriz, puntero o función.  Un identificador es una expresión primaria siempre que se haya declarado como designación de un objeto \(en cuyo caso es un valor L\) o como una función \(en cuyo caso es un designador de función\).  Vea [Expresiones de valor L y de valor R](../c-language/l-value-and-r-value-expressions.md) para ver una definición de valor L.  
  
 El valor de puntero representado por un identificador de matriz no es una variable, por lo que un identificador de matriz no puede formar el operando izquierdo de una operación de asignación y, por lo tanto, no es un valor L modificable.  
  
 Un identificador declarado como una función representa un puntero cuyo valor es la dirección de la función.  El puntero se dirige a una función que devuelve un valor de un tipo especificado.  Así, los identificadores de función tampoco pueden ser valores L en operaciones de asignación.  Para obtener más información, vea [Identificadores](../c-language/c-identifiers.md).  
  
## Vea también  
 [Expresiones primarias de C](../c-language/c-primary-expressions.md)