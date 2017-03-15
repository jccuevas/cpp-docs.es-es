---
title: "abort (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
ms.assetid: 3352bcc4-1a8a-4e1f-8dcc-fe30f6b50f2d
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# abort (Funci&#243;n)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La función **abort**, declarada también en el archivo de inclusión estándar STDLIB.H, finaliza un programa de C\+\+.  La diferencia entre **exit** y **abort** es que **exit** permite que tenga lugar el procesamiento de finalización en tiempo de ejecución de C\+\+ \(se llamará a los destructores de objetos globales\), mientras que **abort** finaliza el programa inmediatamente.  Para obtener más información, vea [abort](../c-runtime-library/reference/abort.md) en la *Referencia de la biblioteca en tiempo de ejecución*.  
  
## Vea también  
 [Finalización del programa](../cpp/program-termination.md)