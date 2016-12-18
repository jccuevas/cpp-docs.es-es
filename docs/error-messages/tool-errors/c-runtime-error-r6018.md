---
title: "Error en tiempo de ejecuci&#243;n de C R6018 | Microsoft Docs"
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
  - "R6018"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "R6018"
ms.assetid: f6dd40d1-a119-4d8b-b39e-97350ea23349
caps.latest.revision: 7
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error en tiempo de ejecuci&#243;n de C R6018
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

error inesperado en el montón  
  
 El programa ha encontrado un error inesperado realizando una operación de administración de memoria.  
  
 Este error suele producirse si el programa modifica sin darse cuenta los datos del montón en tiempo de ejecución.  Sin embargo, también lo puede provocar un error interno en tiempo de ejecución o el código del sistema operativo.  
  
 Si el compilador proporciona una biblioteca que contiene `_heapchk` y `_heapwalk`, se pueden utilizar estas funciones para diagnosticar este error.