---
title: "Asignaci&#243;n simple (C) | Microsoft Docs"
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
  - "operadores de asignación [C++], simples"
  - "conversión de tipos de datos [C++], asignación simple"
  - "signo igual"
  - "operadores [C], asignación simple"
  - "operador de asignación simple"
  - "conversión de tipos [C++], asignación simple"
ms.assetid: e7140a0a-7104-4b3a-b293-7adcc1fdd52b
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Asignaci&#243;n simple (C)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El operador de asignación simple asigna el operando derecho al operando izquierdo.  El valor del operando derecho se convierte al tipo de la expresión de asignación y reemplaza el valor almacenado en el objeto designado por el operando izquierdo.  Se aplican las reglas de conversión para asignación \(vea [Conversiones de asignación](../c-language/assignment-conversions.md)\).  
  
```  
double x;  
int y;  
  
x = y;  
```  
  
 En este ejemplo, el valor de `y` se convierte al tipo **double** y se asigna a `x`.  
  
## Vea también  
 [Operadores de asignación de C](../c-language/c-assignment-operators.md)