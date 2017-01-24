---
title: "Usar abort | Microsoft Docs"
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
  - "Abort"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "abort (función)"
ms.assetid: 3ba39b78-ef74-4a8d-8dee-2d62442de174
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Usar abort
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Al llamar a la función [abort](../c-runtime-library/reference/abort.md), se produce la finalización inmediata.  Omite el proceso de destrucción normal de los objetos estáticos globales inicializados.  También omite cualquier procesamiento especial especificado mediante la función `atexit`.  
  
## Vea también  
 [Consideraciones de finalización adicionales](../cpp/additional-termination-considerations.md)