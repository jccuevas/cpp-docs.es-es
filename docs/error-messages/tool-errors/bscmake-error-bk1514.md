---
title: "Error de BSCMAKE BK1514 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "BK1514"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BK1514"
ms.assetid: 7c7e2504-a490-44ab-bb1f-47385ee2f4b0
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error de BSCMAKE BK1514
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

todos los archivos .SBR están truncados, no se encontró ninguno en nombre de archivo  
  
 Ninguno de los archivos .sbr especificados para una actualización formaron parte del archivo original de información de examen \(.bsc\).  Para buscar los nombres de los archivos .sbr que produjeron este error, lea las advertencias [BK4502](../../error-messages/tool-errors/bscmake-warning-bk4502.md) que lo preceden.  
  
### Posibles causas del error:  
  
1.  Nombre de archivo incorrecto especificado para .sbc o .bsc.  
  
2.  El archivo .bsc dañado requiere que BSCMAKE lo recompile.