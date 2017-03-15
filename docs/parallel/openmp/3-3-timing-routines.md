---
title: "3.3 Timing Routines | Microsoft Docs"
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
ms.assetid: 21060d64-cbe8-4e38-8718-3a68d6a57be3
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.3 Timing Routines
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las funciones descritas en esta sección admiten un temporizador portable de reloj:  
  
-   La función de `omp_get_wtime` devuelve tiempo transcurrido de reloj.  
  
-   la función de `omp_get_wtick` devuelve segundos entre los tic\-tac de reloj sucesivos.