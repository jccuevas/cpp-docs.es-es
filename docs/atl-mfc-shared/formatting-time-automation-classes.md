---
title: "Formatting Time: Automation Classes | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Automation classes, formatting time"
  - "formatting [C++], hora"
  - "time [C++], aplicar formato"
ms.assetid: 155c5bef-b555-4bed-9545-29afc49715f1
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Formatting Time: Automation Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

#### Para dar formato a una hora  
  
1.  Utilice la función miembro de **Formato** de [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) o de [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md) para crear una cadena de caracteres que representa el tiempo o de tiempo transcurrido.  
  
     [!code-cpp[NVC_ATLMFC_Utilities#179](../atl-mfc-shared/codesnippet/CPP/formatting-time-automation-classes_1.cpp)]  
  
 Para obtener más información, vea la clase [COleVariant](../mfc/reference/colevariant-class.md).  
  
### ¿Qué más desea saber?  
  
-   [Programación general de fecha y hora en MFC](../atl-mfc-shared/date-and-time.md)  
  
-   [Clases de propósito general para la programación de fecha y hora](../atl-mfc-shared/date-and-time-general-purpose-classes.md)  
  
-   [Trabajar con SYSTEMTIME](../atl-mfc-shared/date-and-time-systemtime-support.md)  
  
## Vea también  
 [Date and Time: Automation Support](../atl-mfc-shared/date-and-time-automation-support.md)