---
title: "Date and Time | Microsoft Docs"
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
  - "fechas, MFC"
  - "MFC, fecha y hora"
  - "hora"
  - "hora, programación en MFC"
ms.assetid: ecf56dc5-d418-4603-ad3e-af7e205a6403
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Date and Time
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC admite varias maneras de trabajar con fechas y horas.  Incluyen los siguientes:  
  
-   Clases de uso general de tiempo.  Las clases de [CTime](../atl-mfc-shared/reference/ctime-class.md) y de [CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md) encapsulan la mayor parte de la funcionalidad asociada a la biblioteca de hora estándar, que se declara en TIME.H.  
  
-   Compatibilidad con el reloj del sistema.  Con la versión 3,0 de MFC, compatibilidad se agregó a `CTime` para Win32 `SYSTEMTIME` y los tipos de datos de `FILETIME` .  
  
-   Compatibilidad con la automatización [Tipo de datos de la DATE](../atl-mfc-shared/date-type.md).  **DATE** admite la fecha, la hora, y la valores de fecha y hora.  las clases de [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) y de [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md) encapsulan esta funcionalidad.  Ejecuta la clase de [COleVariant](../mfc/reference/colevariant-class.md) utilizando la compatibilidad de automatización.  
  
## ¿Qué más desea saber?  
  
-   [fecha y hora: Clases de uso general](../atl-mfc-shared/date-and-time-general-purpose-classes.md)  
  
-   [fecha y hora: Compatibilidad SYSTEMTIME](../atl-mfc-shared/date-and-time-systemtime-support.md)  
  
-   [fecha y hora: Compatibilidad de automatización](../atl-mfc-shared/date-and-time-automation-support.md)  
  
-   [fecha y hora: Compatib. con bases de datos](../atl-mfc-shared/date-and-time-database-support.md)  
  
## Vea también  
 [Conceptos](../mfc/mfc-concepts.md)   
 [Temas generales de MFC](../mfc/general-mfc-topics.md)