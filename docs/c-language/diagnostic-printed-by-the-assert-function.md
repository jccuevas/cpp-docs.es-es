---
title: "Diagn&#243;stico impreso por la funci&#243;n assert | Microsoft Docs"
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
ms.assetid: 78b64200-520d-40da-9a61-71553f411d4f
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Diagn&#243;stico impreso por la funci&#243;n assert
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 4.2** El diagnóstico impreso por, y el comportamiento de finalización de, la función **assert**  
  
 La función **assert** imprime un mensaje de diagnóstico y llama a la rutina **abort** si la expresión es false \(0\).  El mensaje de diagnóstico tiene la forma  
  
 **Error de aserción**: *expression***, archivo** *filename***, línea** *linenumber*  
  
 donde filename es el nombre del archivo de código fuente y linenumber es el número de línea de la aserción que produjo un error en el archivo de código fuente.  No se realiza ninguna acción si la expresión es true \(distinto de cero\).  
  
## Vea también  
 [Funciones de la biblioteca](../c-language/library-functions.md)