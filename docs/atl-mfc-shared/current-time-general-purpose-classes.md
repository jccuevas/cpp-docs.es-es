---
title: "Current Time: General Purpose Classes | Microsoft Docs"
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
  - "hora actual, CTime object"
  - "inicializar objetos, with the current time"
  - "procedimientos, getting current time"
  - "hora, getting current"
  - "hora, setting current"
ms.assetid: c39e6775-6a92-4b27-95a7-5c86ed371d8a
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Current Time: General Purpose Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El siguiente procedimiento muestra cómo crear un objeto de `CTime` e inicialícela con la hora actual.  
  
#### para obtener la hora actual  
  
1.  Asigna un objeto de `CTime` , como sigue:  
  
     [!code-cpp[NVC_ATLMFC_Utilities#171](../atl-mfc-shared/codesnippet/CPP/current-time-general-purpose-classes_1.cpp)]  
  
    > [!NOTE]
    >  Los objetos sin inicializar de `CTime` no se inicializan en una hora válido.  
  
2.  Llame a la función de `CTime::GetCurrentTime` para obtener la hora actual del sistema operativo.  Esta función devuelve un objeto de `CTime` que se puede utilizar para establecer el valor de `CTime`, como sigue:  
  
     [!code-cpp[NVC_ATLMFC_Utilities#172](../atl-mfc-shared/codesnippet/CPP/current-time-general-purpose-classes_2.cpp)]  
  
     Puesto que `GetCurrentTime` es una función miembro estática de la clase de `CTime` , debe calificar su nombre con el nombre de la clase y el operador de resolución de ámbito \(`::`\), `CTime::GetCurrentTime()`.  
  
 Por supuesto, los dos pasos descritos anteriormente se pueden combinar en una única instrucción de programa como sigue:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#173](../atl-mfc-shared/codesnippet/CPP/current-time-general-purpose-classes_3.cpp)]  
  
## Vea también  
 [Date and Time: General\-Purpose Classes](../atl-mfc-shared/date-and-time-general-purpose-classes.md)