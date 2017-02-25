---
title: "CTimeSpan Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CTimeSpan"
  - "CTimeSpan"
  - "timespan"
  - "ATL::CTimeSpan"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTimeSpan class"
  - "tiempo transcurrido, CTimeSpan object"
  - "shared classes, CTimeSpan"
  - "time span"
  - "hora, elapsed"
  - "timespan"
ms.assetid: ee1e42f6-1839-477a-8435-fb26ad475140
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CTimeSpan Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Un tiempo, que internamente se almacena como el número de segundos de la duración.  
  
## Sintaxis  
  
```  
class CTimeSpan  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CTimeSpan::CTimeSpan](../Topic/CTimeSpan::CTimeSpan.md)|Crea los objetos de `CTimeSpan` de varias maneras.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CTimeSpan::Format](../Topic/CTimeSpan::Format.md)|Convierte `CTimeSpan` en una cadena con formato.|  
|[CTimeSpan::GetDays](../Topic/CTimeSpan::GetDays.md)|Devuelve un valor que representa el número de días completos en este `CTimeSpan`.|  
|[CTimeSpan::GetHours](../Topic/CTimeSpan::GetHours.md)|Devuelve un valor que representa el número de horas del día actual \(– 23 a 23\).|  
|[CTimeSpan::GetMinutes](../Topic/CTimeSpan::GetMinutes.md)|Devuelve un valor que representa el número de minutos de la hora actual \(– 59 a 59\).|  
|[CTimeSpan::GetSeconds](../Topic/CTimeSpan::GetSeconds.md)|Devuelve un valor que representa el número de segundos del minuto actual \(– 59 a 59\).|  
|[CTimeSpan::GetTimeSpan](../Topic/CTimeSpan::GetTimeSpan.md)|Devuelve el valor del objeto `CTimeSpan`.|  
|[CTimeSpan::GetTotalHours](../Topic/CTimeSpan::GetTotalHours.md)|Devuelve un valor que representa el número total de horas completadas en este `CTimeSpan`.|  
|[CTimeSpan::GetTotalMinutes](../Topic/CTimeSpan::GetTotalMinutes.md)|Devuelve un valor que representa el número de minutos completos en este `CTimeSpan`.|  
|[CTimeSpan::GetTotalSeconds](../Topic/CTimeSpan::GetTotalSeconds.md)|Devuelve un valor que representa el número de segundos completos en este `CTimeSpan`.|  
|[CTimeSpan::Serialize64](../Topic/CTimeSpan::Serialize64.md)|Serializa los datos a o desde un archivo.|  
  
### Operadores  
  
|||  
|-|-|  
|[operador \+ –](../Topic/CTimeSpan::operator%20+,%20-.md)|Suma y resta los objetos de `CTimeSpan` .|  
|[operador \+\= – \=](../Topic/CTimeSpan::operator%20+=,%20-=.md)|Suma y resta un objeto de `CTimeSpan` a y desde este `CTimeSpan`.|  
|[operator \=\= \< etc..](../Topic/CTimeSpan%20Comparison%20Operators.md)|compara dos valores de hora relativos.|  
  
## Comentarios  
 `CTimeSpan` no tiene una clase base.  
  
 las funciones de`CTimeSpan` convierten segundos a las distintas combinaciones de días, de horas, de minutos, y de segundos.  
  
 el objeto de `CTimeSpan` se almacena en una estructura de **\_\_time64\_t** , que es 8 bytes.  
  
 Una clase complementaria, [CTime](../../atl-mfc-shared/reference/ctime-class.md), representa un tiempo absoluto.  
  
 Las clases de `CTime` y de `CTimeSpan` no están diseñados para la derivación.  Porque no hay funciones virtuales, el tamaño de ambos objetos de `CTime` y de `CTimeSpan` es 8 bytes.  La mayoría de las funciones miembro inline.  
  
 Para obtener más información sobre cómo utilizar `CTimeSpan`, vea los artículos [fecha y hora](../../atl-mfc-shared/date-and-time.md), y [administración de tiempo](../../c-runtime-library/time-management.md) en *la referencia de la biblioteca en tiempo de ejecución*.  
  
## Requisitos  
 **encabezado:** atltime.h  
  
## Vea también  
 [asctime, \_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [\_ftime, \_ftime32, \_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime, \_gmtime32, \_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime, \_localtime32, \_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [strftime, wcsftime, \_strftime\_l, \_wcsftime\_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)   
 [time, \_time32, \_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [ATL\/MFC Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)