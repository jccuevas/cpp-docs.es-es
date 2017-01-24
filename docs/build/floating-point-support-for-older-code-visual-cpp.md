---
title: "Compatibilidad del c&#243;digo antiguo con puntos flotantes (Visual C++) | Microsoft Docs"
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
ms.assetid: a2a26b96-7bc2-418a-981a-51aa1a0294a2
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Compatibilidad del c&#243;digo antiguo con puntos flotantes (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los registros MMX y de pila de punto flotante \(MM0\-MM7\/ST0\-ST7\) se conservan mediante cambios de contexto.  No existe una convención de llamadas explícitas para estos registros.  El uso de estos registros está estrictamente prohibido en código en modo kernel.  
  
## Vea también  
 [Convención de llamada](../build/calling-convention.md)