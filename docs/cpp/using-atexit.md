---
title: "Usar atexit | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "atexit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "atexit (función)"
ms.assetid: d28fda17-c3d4-4af6-ba44-f44886bbb237
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Usar atexit
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Con la función [atexit](../c-runtime-library/reference/atexit.md), puede especificar una función de procesamiento de salida que se ejecute antes de la finalización del programa.  Los objetos estáticos no globales inicializados antes de la llamada a `atexit` se destruyen antes de la ejecución de la función de procesamiento de salida.  
  
## Vea también  
 [Consideraciones de finalización adicionales](../cpp/additional-termination-considerations.md)