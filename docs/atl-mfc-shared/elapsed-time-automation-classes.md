---
title: "Elapsed Time: Automation Classes | Microsoft Docs"
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
  - "adding dates"
  - "Automation classes, tiempo transcurrido"
  - "calculating dates and times"
  - "cálculos, fecha y hora"
  - "fechas, calculating intervals"
  - "tiempo transcurrido, calculating in Automation"
  - "intervals, fecha y hora"
  - "hora, elapsed"
ms.assetid: 26b34b37-c10e-4b91-82c3-1dc5ffb5361f
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Elapsed Time: Automation Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este procedimiento muestra cómo calcular la diferencia entre dos objetos de `CTime` y obtener el resultado de `CTimeSpan` .  
  
#### Para calcular el tiempo transcurrido  
  
1.  Cree dos objetos de `COleDateTime` .  
  
2.  Establezca uno de los objetos de `COleDateTime` en la hora actual.  
  
3.  Realice alguna tarea larga.  
  
4.  Establezca el otro objeto de `COleDateTime` en la hora actual.  
  
5.  Toma la diferencia entre los dos veces.  
  
     [!code-cpp[NVC_ATLMFC_Utilities#178](../atl-mfc-shared/codesnippet/CPP/elapsed-time-automation-classes_1.cpp)]  
  
## Vea también  
 [Date and Time: Automation Support](../atl-mfc-shared/date-and-time-automation-support.md)