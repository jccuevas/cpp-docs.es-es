---
title: "Error de las herramientas del vinculador LNK1245 | Microsoft Docs"
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
  - "LNK1245"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1245"
ms.assetid: 179c8165-ffbb-44cd-9f24-5250f29577cc
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error de las herramientas del vinculador LNK1245
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

subsistema 'subsistema' no válido especificado; \/SUBSYSTEM debe ser WINDOWS, WINDOWSCE o CONSOLE  
  
 Se ha utilizado [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) para compilar el objeto y una de las siguientes condiciones era cierta:  
  
-   Se ha definido un punto de entrada personalizado \([\/ENTRY](../../build/reference/entry-entry-point-symbol.md)\), de manera que el vinculador no ha podido inferir un subsistema.  
  
-   Se ha pasado un valor a la opción del vinculador [\/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) que no es válido para objetos \/clr.  
  
 En ambos casos, la solución consiste en especificar un valor válido para la opción del vinculador \/SUBSYSTEM.