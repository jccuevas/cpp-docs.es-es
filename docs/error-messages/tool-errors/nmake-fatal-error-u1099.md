---
title: "Error grave de NMAKE U1099 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "U1099"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1099"
ms.assetid: 6688a805-43e6-4247-a2d0-14be082f0b13
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error grave de NMAKE U1099
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

desbordamiento de pila  
  
 El archivo MAKE en proceso es demasiado complejo para la asignación actual de pila en NMAKE.  NMAKE tiene una asignación de 0x3000 \(12 KB\).  
  
 Para aumentar la asignación de pila de NMAKE, ejecute la utilidad [editbin \/stack](../../build/reference/stack.md) con una opción de pila superior:  
  
 **editbin \/STACK:reserve NMAKE.EXE**  
  
 donde *reserve* es un número mayor que la actual asignación de pila de NMAKE.