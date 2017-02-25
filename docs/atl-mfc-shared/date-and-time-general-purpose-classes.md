---
title: "Date and Time: General-Purpose Classes | Microsoft Docs"
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
  - "date and time classes"
  - "time classes"
ms.assetid: b8115d7f-428a-4c41-9970-18502f2caca2
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Date and Time: General-Purpose Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se describe cómo aprovechar los servicios de uso general de la biblioteca de clases relacionados hasta la fecha y la administración de tiempo.  Incluyen descrita procedimientos:  
  
-   [obtener la hora actual](../atl-mfc-shared/current-time-general-purpose-classes.md)  
  
-   [Tiempo transcurrido](../atl-mfc-shared/elapsed-time-general-purpose-classes.md)  
  
-   [Dar formato a una representación de cadena de una fecha o una hora](../atl-mfc-shared/formatting-time-values-general-purpose-classes.md)  
  
 La clase de `CTime` proporciona una manera de representar la información de fecha y hora con facilidad.  La clase de `CTimeSpan` representa el tiempo transcurrido, como la diferencia entre dos objetos de `CTime` .  
  
> [!NOTE]
>  Los objetos de CTime se pueden utilizar para representar fechas entre el 1 de enero de 1970 y el 18 de enero de 2038.  los objetos de`CTime` tienen una resolución de 1 segundo.  `CTime` se basa en el tipo de datos `time_t` , definido en *la referencia de la biblioteca en tiempo de ejecución*.  
  
## Vea también  
 [Date and Time](../atl-mfc-shared/date-and-time.md)