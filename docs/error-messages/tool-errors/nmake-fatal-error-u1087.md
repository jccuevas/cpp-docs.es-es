---
title: "Error grave de NMAKE U1087 | Microsoft Docs"
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
  - "U1087"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1087"
ms.assetid: 5236ab54-e117-484d-99c3-852b061fd3d0
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error grave de NMAKE U1087
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se pueden tener dependientes : y :: para el mismo destino  
  
 Un destino no se puede especificar en una dependencia de signo de dos puntos \(**:**\) y de signo doble de dos puntos \(`::`\).  
  
 Para especificar un destino en varios bloques de descripciones, utilice `::` en cada línea de dependencia.