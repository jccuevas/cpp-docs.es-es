---
title: "_CRT_DISABLE_PERFCRIT_LOCKS | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_CRT_DISABLE_PERFCRIT_LOCKS"
  - "CRT_DISABLE_PERFCRIT_LOCKS"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_CRT_DISABLE_PERFCRIT_LOCKS (constante)"
  - "CRT_DISABLE_PERFCRIT_LOCKS (constante)"
ms.assetid: 36cc2d86-cdb1-4b2b-a03c-c0d3818e7c6f
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _CRT_DISABLE_PERFCRIT_LOCKS
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Deshabilita el bloqueo rendimiento\- fundamental en operaciones de E\/S.  
  
## Sintaxis  
  
```  
#define _CRT_DISABLE_PERFCRIT_LOCKS  
```  
  
## Comentarios  
 La definición de este símbolo puede mejorar el rendimiento en programas de un único subproceso de E\/S forzando todas las operaciones de E\/S adopte un modelo con un único subproceso de E\/S.  Para obtener más información, vea [Rendimiento de bibliotecas multiproceso](../c-runtime-library/multithreaded-libraries-performance.md).  
  
## Vea también  
 [Constantes globales](../c-runtime-library/global-constants.md)