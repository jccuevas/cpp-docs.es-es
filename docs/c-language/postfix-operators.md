---
title: "Operadores postfijos | Microsoft Docs"
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
  - "operadores [C], postfijo"
  - "operadores postfijos"
ms.assetid: 76260011-1624-484e-8bef-72ae7ab556cc
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Operadores postfijos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los operadores de postfijo tienen la máxima prioridad \(el enlace más estricto\) en la evaluación de una expresión.  
  
## Sintaxis  
 *postfix\-expression*:  
 *primary\-expression*  
  
 *postfix\-expression*  **\[**  *expression*  **\]**  
  
 *postfix\-expression*  **\(**  *argument\-expression\-list*  opt **\)**  
  
 *postfix\-expression*  **.**  *identifier*  
  
 *postfix\-expression*  **–\>**  *identifier*  
  
 *postfix\-expression*  **\+\+**  
  
 *postfix\-expression*  **––**  
  
 Los operadores en este nivel de prioridad son los subíndices de matriz, las llamadas a función, los miembros de estructura y unión, y los operadores postfijos de incremento y decremento.  
  
## Vea también  
 [Operadores de C](../c-language/c-operators.md)