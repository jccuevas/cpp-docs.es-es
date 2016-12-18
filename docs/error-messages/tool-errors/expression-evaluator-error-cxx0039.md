---
title: "Error del evaluador de expresiones CXX0039 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "CXX0039"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAN0039"
  - "CXX0039"
ms.assetid: 8bf698d2-e015-4595-944f-72b81aa43d22
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del evaluador de expresiones CXX0039
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

símbolo ambiguo  
  
 El evaluador de la expresión C no puede determinar la instancia de un símbolo que se debe utilizar en una expresión.  El símbolo aparece más de una vez en el árbol de herencia.  
  
 Se debe usar el operador de resolución de ámbito \(`::`\) para especificar explícitamente la instancia que se utiliza en la expresión.  
  
 Este error es idéntico a CAN00039.