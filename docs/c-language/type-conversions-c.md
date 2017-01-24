---
title: "Conversiones de tipos (C) | Microsoft Docs"
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
  - "conversiones, tipo"
  - "convertir tipos"
  - "promociones de enteros"
  - "conversiones de tipos, momento de realización"
  - "conversión de tipos"
ms.assetid: d130ee7c-03c3-48f4-af7b-1fdba0d3b086
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Conversiones de tipos (C)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las conversiones de tipos dependen del operador especificado y del tipo del operando o de los operadores.  Las conversiones de tipos se realizan en los casos siguientes:  
  
-   Cuando se asigna un valor de un tipo a una variable de un tipo diferente o un operador convierte el tipo del operando o los operandos antes de realizar una operación  
  
-   Cuando un valor de un tipo se convierte explícitamente a un tipo diferente  
  
-   Cuando se pasa un valor como argumento a una función o cuando se devuelve un tipo de una función  
  
 Un carácter, un entero corto o un campo de bits entero, todos con signo o sin él o un tipo de objeto o de enumeración se pueden usar en una expresión siempre que se pueda usar un entero.  Si `int` puede representar todos los valores del tipo original, el valor se convierte en `int`; si no, se convierte en `unsigned int`.  Este proceso se denomina “promoción entera”. Las promociones enteras conservan el valor.  Es decir, se garantiza que el valor después de la promoción es igual que el valor antes de la promoción.  Vea [Conversiones aritméticas usuales](../c-language/usual-arithmetic-conversions.md) para obtener más información.  
  
## Vea también  
 [Expresiones y asignaciones](../c-language/expressions-and-assignments.md)