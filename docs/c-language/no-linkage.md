---
title: "Sin vinculaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "vinculación [C++], ninguna"
  - "sin vinculación"
ms.assetid: 5a413082-1034-4e04-b76b-8d14668bf434
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Sin vinculaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si una declaración de un identificador dentro de un bloque no incluye el especificador de clase de almacenamiento `extern`, el identificador no tiene ninguna vinculación y es exclusivo de la función.  
  
 Los identificadores siguientes no tienen vinculación:  
  
-   Un identificador declarado como algo distinto de un objeto o función  
  
-   Un identificador declarado como un parámetro de función  
  
-   Un identificador de ámbito de bloque para un objeto declarado sin el especificador de clase de almacenamiento `extern`  
  
 Si un identificador no tiene vinculación, al volver a declararse el mismo nombre \(en un especificador de declarador o tipo\) en el mismo nivel de ámbito, se genera un error de redefinición de símbolo.  
  
## Vea también  
 [Usar extern para especificar la vinculación](../cpp/using-extern-to-specify-linkage.md)