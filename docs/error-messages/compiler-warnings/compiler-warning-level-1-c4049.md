---
title: "Advertencia del compilador (nivel 1) C4049 | Microsoft Docs"
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
  - "C4049"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4049"
ms.assetid: d11c1870-bcfc-4d71-8945-b87ec6ec3514
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4049
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

límite del compilador: se va a finalizar la emisión de números de línea  
  
 El archivo contiene más de 16.777.215 \(2<sup>24</sup>\-1\) líneas de código fuente.  El compilador detiene la numeración en 16.777.215.  
  
 Para código posterior a la línea 16.777.215:  
  
-   La imagen no contendrá información de depuración de números de línea.  
  
-   Algunos diagnósticos pueden presentar números de línea incorrectos.  
  
-   Las listas de .asm \(\/Fas\) pueden tener números de línea incorrectos.