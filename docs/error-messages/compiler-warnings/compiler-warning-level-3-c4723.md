---
title: "Advertencia del compilador (nivel 3) C4723 | Microsoft Docs"
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
  - "C4723"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4723"
ms.assetid: 07669d14-3fd8-4a43-94bc-b61c50e58460
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 3) C4723
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

posible división por 0  
  
 El segundo operando de una operación de división se evalúa como cero en tiempo de compilación, dando resultados no definidos.  
  
 Esta advertencia se genera sólo al utilizar [\/Og](../../build/reference/og-global-optimizations.md) o una opción de optimización que implique \/Og.  
  
 Puede que el compilador haya generado el operando cero.