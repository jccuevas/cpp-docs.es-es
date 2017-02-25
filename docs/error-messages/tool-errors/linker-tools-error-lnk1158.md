---
title: "Error de las herramientas del vinculador LNK1158 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1158"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1158"
ms.assetid: 45febf16-d9e1-42db-af91-532e2717fd6a
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error de las herramientas del vinculador LNK1158
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se puede ejecutar 'nombredearchivo'  
  
 El archivo ejecutable dado al que llama [LINK](../../build/reference/linker-command-line-syntax.md) no se encuentra en el directorio que contiene LINK, ni tampoco en ninguno de los directorios especificados en la variable de entorno PATH.  
  
 Por ejemplo, se obtiene este error si se intenta utilizar el parámetro PGOPTIMIZE de la opción del vinculador [\/LTCG](../../build/reference/ltcg-link-time-code-generation.md) en un equipo con un sistema operativo de 32 bits.