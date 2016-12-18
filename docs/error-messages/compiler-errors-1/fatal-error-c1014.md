---
title: "Error irrecuperable C1014 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C1014"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1014"
ms.assetid: 4c01ef70-e765-4d07-a3fe-a11c19fb610b
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error irrecuperable C1014
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Hay demasiados archivos de inclusión: profundidad \= nivel  
  
 El anidamiento de directivas `#include` es demasiado profundo. Las directivas anidadas pueden incluir archivos abiertos. El archivo de código fuente que contiene la directiva se cuenta como un archivo.