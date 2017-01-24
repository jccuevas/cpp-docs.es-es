---
title: "Advertencia de las herramientas del vinculador LNK4010 | Microsoft Docs"
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
  - "LNK4010"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4010"
ms.assetid: 2824cf99-4174-4b60-a6e2-c01e9f1ee52d
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia de las herramientas del vinculador LNK4010
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

número de versión del subsistema número no válido; se ha supuesto la versión predeterminada del subsistema  
  
 Puede especificar una versión para el subsistema de la imagen \([\/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md)\).  Cada subsistema tiene un requisito mínimo de versión.  Si la versión especificada es inferior a la mínima, se producirá esta advertencia y el vinculador utilizará el subsistema predeterminado.