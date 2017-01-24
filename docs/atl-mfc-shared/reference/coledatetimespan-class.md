---
title: "COleDateTimeSpan Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.COleDateTimeSpan"
  - "COleDateTimeSpan"
  - "ATL::COleDateTimeSpan"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleDateTimeSpan class"
  - "Date (tipo de datos), MFC encapsulation of"
  - "shared classes, COleDateTimeSpan"
  - "time span"
  - "timespan"
ms.assetid: 7441526d-a30a-4019-8fb3-3fee6f897cbe
caps.latest.revision: 19
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleDateTimeSpan Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa una hora relativo, una duración.  
  
## Sintaxis  
  
```  
class COleDateTimeSpan  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleDateTimeSpan::COleDateTimeSpan](../Topic/COleDateTimeSpan::COleDateTimeSpan.md)|Crea un objeto `COleDateTimeSpan`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleDateTimeSpan::Format](../Topic/COleDateTimeSpan::Format.md)|Genera una representación de cadena con formato de un objeto de `COleDateTimeSpan` .|  
|[COleDateTimeSpan::GetDays](../Topic/COleDateTimeSpan::GetDays.md)|Devuelve la parte del día del intervalo que este objeto de `COleDateTimeSpan` representa.|  
|[COleDateTimeSpan::GetHours](../Topic/COleDateTimeSpan::GetHours.md)|Devuelve la parte de hora del intervalo que este objeto de `COleDateTimeSpan` representa.|  
|[COleDateTimeSpan::GetMinutes](../Topic/COleDateTimeSpan::GetMinutes.md)|Devuelve la parte minuciosa span que este objeto de `COleDateTimeSpan` representa.|  
|[COleDateTimeSpan::GetSeconds](../Topic/COleDateTimeSpan::GetSeconds.md)|Devuelve a la segunda parte del intervalo que este objeto de `COleDateTimeSpan` representa.|  
|[COleDateTimeSpan::GetStatus](../Topic/COleDateTimeSpan::GetStatus.md)|obtiene el estado \(validez\) de este objeto de `COleDateTimeSpan` .|  
|[COleDateTimeSpan::GetTotalDays](../Topic/COleDateTimeSpan::GetTotalDays.md)|devuelve el número de días que este objeto de `COleDateTimeSpan` representa.|  
|[COleDateTimeSpan::GetTotalHours](../Topic/COleDateTimeSpan::GetTotalHours.md)|devuelve el número de horas que este objeto de `COleDateTimeSpan` representa.|  
|[COleDateTimeSpan::GetTotalMinutes](../Topic/COleDateTimeSpan::GetTotalMinutes.md)|devuelve el número de minutos que este objeto de `COleDateTimeSpan` representa.|  
|[COleDateTimeSpan::GetTotalSeconds](../Topic/COleDateTimeSpan::GetTotalSeconds.md)|devuelve el número de segundos que este objeto de `COleDateTimeSpan` representa.|  
|[COleDateTimeSpan::SetDateTimeSpan](../Topic/COleDateTimeSpan::SetDateTimeSpan.md)|establece el valor de este objeto de `COleDateTimeSpan` .|  
|[COleDateTimeSpan::SetStatus](../Topic/COleDateTimeSpan::SetStatus.md)|establece el estado \(validez\) de este objeto de `COleDateTimeSpan` .|  
  
### Operadores públicos  
  
|||  
|-|-|  
|[operador \+, \-](../Topic/COleDateTimeSpan::operator%20+,%20-.md)|Add, subtract, y cambie el signo por valores de `COleDateTimeSpan` .|  
|[operador \+\=, \- \=](../Topic/COleDateTimeSpan::operator%20+=,%20-=.md)|Agregue y restar un valor de `COleDateTimeSpan` de este valor de `COleDateTimeSpan` .|  
|[operador \=](../Topic/COleDateTimeSpan::operator%20=.md)|copia un valor de `COleDateTimeSpan` .|  
|[operator \=\=, \<, \<\=](../Topic/COleDateTimeSpan%20Relational%20Operators.md)|Compara dos valores de `COleDateTimeSpan` .|  
|[doble de operador](../Topic/COleDateTimeSpan::operator%20double.md)|convierte este valor de `COleDateTimeSpan` a **Doble**.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleDateTimeSpan::m\_span](../Topic/COleDateTimeSpan::m_span.md)|contiene **Doble** subyacente para este objeto de `COleDateTimeSpan` .|  
|[COleDateTimeSpan::m\_status](../Topic/COleDateTimeSpan::m_status.md)|contiene el estado de este objeto de `COleDateTimeSpan` .|  
  
## Comentarios  
 `COleDateTimeSpan` no tiene una clase base.  
  
 `COleDateTimeSpan` conserva tiempo en días.  
  
 `COleDateTimeSpan` se utiliza con la clase [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)complementarias.  `COleDateTime` encapsula el tipo de datos de **DATE** de automatización OLE.  `COleDateTime` representa valores de hora absolutos.  todos los cálculos de `COleDateTime` implicar los valores de `COleDateTimeSpan` .  La relación entre estas clases es parecida a la que está entre [CTime](../../atl-mfc-shared/reference/ctime-class.md) y [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md).  
  
 Para obtener más información sobre las clases de `COleDateTime` y de `COleDateTimeSpan` , vea el artículo [fecha y hora: Compatibilidad de automatización](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
## Requisitos  
 **encabezado:** ATLComTime.h  
  
## Vea también  
 [COleDateTime Class](../../atl-mfc-shared/reference/coledatetime-class.md)   
 [CTime Class](../../atl-mfc-shared/reference/ctime-class.md)   
 [CTimeSpan Class](../../atl-mfc-shared/reference/ctimespan-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [ATL\/MFC Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)