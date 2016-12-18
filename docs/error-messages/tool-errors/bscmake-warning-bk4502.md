---
title: "Advertencia de BSCMAKE BK4502 | Microsoft Docs"
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
  - "BK4502"
  - "BK1513"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BK1513"
  - "BK4502"
ms.assetid: ee412ec8-df03-4cdb-91ee-5d609ded8691
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia de BSCMAKE BK4502
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

el archivo .SBR truncado 'nombredearchivo' no está en 'nombredearchivo'  
  
 Se ha especificado un archivo .sbr de longitud cero que no pertenecía originalmente al archivo .bsc durante una actualización.  
  
### Posibles causas del error:  
  
1.  Nombre de archivo especificado incorrecto.  
  
2.  Archivo eliminado. \(Error [BK1513](../../error-messages/tool-errors/bscmake-error-bk1513.md)\).  
  
3.  Archivo dañado que requiere que BSCMAKE realice una nueva compilación completa.