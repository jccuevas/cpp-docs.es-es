---
title: "Elapsed Time: General-Purpose Classes | Microsoft Docs"
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
  - "calculating dates and times"
  - "cálculos, fecha y hora"
  - "fechas, calculating intervals"
  - "tiempo transcurrido"
  - "tiempo transcurrido, calcular"
  - "intervals, fecha y hora"
  - "hora, elapsed"
ms.assetid: e5c5d3d2-ce1d-409e-875c-98848434e716
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Elapsed Time: General-Purpose Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El siguiente procedimiento muestra cómo calcular la diferencia entre dos objetos de `CTime` y obtener el resultado de `CTimeSpan` .  
  
#### Para calcular el tiempo transcurrido  
  
1.  Utilice objetos de `CTime` y de `CTimeSpan` para calcular el tiempo transcurrido, como sigue:  
  
     [!code-cpp[NVC_ATLMFC_Utilities#174](../atl-mfc-shared/codesnippet/CPP/elapsed-time-general-purpose-classes_1.cpp)]  
  
     Una vez que se ha calculado `elapsedTime`, puede utilizar las funciones miembro de `CTimeSpan` para extraer los componentes del valor de tiempo transcurrido.  
  
## Vea también  
 [Date and Time: General\-Purpose Classes](../atl-mfc-shared/date-and-time-general-purpose-classes.md)