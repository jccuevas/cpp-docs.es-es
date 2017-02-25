---
title: "Current Time: Automation Classes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Automation classes, hora actual"
  - "hora actual, COleDateTime object"
  - "procedimientos, getting current time"
  - "hora, getting current"
  - "hora, setting current"
ms.assetid: cc967f17-1189-4cf3-85f9-1969462d5f72
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Current Time: Automation Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El siguiente procedimiento muestra cómo crear un objeto de `COleDateTime` e inicialícela con la hora actual.  
  
#### para obtener la hora actual  
  
1.  Crear un objeto `COleDateTime`.  
  
2.  Llamar a `GetCurrentTime`.  
  
     [!code-cpp[NVC_ATLMFC_Utilities#177](../atl-mfc-shared/codesnippet/CPP/current-time-automation-classes_1.cpp)]  
  
## Vea también  
 [Date and Time: Automation Support](../atl-mfc-shared/date-and-time-automation-support.md)