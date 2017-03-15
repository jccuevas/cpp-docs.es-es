---
title: "Error de las herramientas del vinculador LNK1223 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1223"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1223"
ms.assetid: c4728c36-daee-462f-a1c7-8733dcdec88e
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error de las herramientas del vinculador LNK1223
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

archivo no válido o dañado: el archivo contiene contribuciones .pdata no válidas  
  
 En el caso de plataformas RISC que utilizan pdata, este error se produce si el compilador generó una sección .pdata con entradas no ordenadas.  
  
 Para solucionar este problema, intente compilar sin habilitar [\/GL \(Whole Program Optimization\)](../../error-messages/tool-errors/linker-tools-error-lnk1223.md).  Los cuerpos de función vacíos también pueden producir este error en algunos casos.