---
title: "CTime Class | Microsoft Docs"
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
  - "ATL.CTime"
  - "CTime"
  - "ATL::CTime"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTime class"
  - "shared classes, CTime"
ms.assetid: 0a299544-485b-48dc-9d3c-fdc30f57d612
caps.latest.revision: 30
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CTime Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

representa una hora y una fecha absolutas.  
  
## Sintaxis  
  
```  
class CTime  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CTime::CTime](../Topic/CTime::CTime.md)|Crea los objetos de `CTime` de varias maneras.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CTime::Format](../Topic/CTime::Format.md)|Convierte un objeto de `CTime` en una cadena con formato basada en la zona horaria local.|  
|[CTime::FormatGmt](../Topic/CTime::FormatGmt.md)|Convierte un objeto de `CTime` en una cadena con formato basada en hora UTC.|  
|[CTime::GetAsDBTIMESTAMP](../Topic/CTime::GetAsDBTIMESTAMP.md)|Convierte la información de tiempo almacenada en el objeto de `CTime` a una estructura de Win32\-compatible <xref:System.Data.OleDb.OleDbType> .|  
|[CTime::GetAsSystemTime](../Topic/CTime::GetAsSystemTime.md)|Convierte la información de tiempo almacenada en el objeto de `CTime` a una estructura de Win32\-compatible [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) .|  
|[CTime::GetCurrentTime](../Topic/CTime::GetCurrentTime.md)|Crea un objeto de `CTime` que representa la hora actual \(función miembro estática\).|  
|[CTime::GetDay](../Topic/CTime::GetDay.md)|devuelve el día representan por el objeto de `CTime` .|  
|[CTime::GetDayOfWeek](../Topic/CTime::GetDayOfWeek.md)|devuelve el día de la semana representada por el objeto de `CTime` .|  
|[CTime::GetGmtTm](../Topic/CTime::GetGmtTm.md)|Analiza un objeto de `CTime` en componentes — basados en hora UTC.|  
|[CTime::GetHour](../Topic/CTime::GetHour.md)|devuelve la hora representada por el objeto de `CTime` .|  
|[CTime::GetLocalTm](../Topic/CTime::GetLocalTm.md)|Analiza un objeto de `CTime` en componentes — según la zona horaria local.|  
|[CTime::GetMinute](../Topic/CTime::GetMinute.md)|devuelve el minuto representado por el objeto de `CTime` .|  
|[CTime::GetMonth](../Topic/CTime::GetMonth.md)|devuelve el mes representado por el objeto de `CTime` .|  
|[CTime::GetSecond](../Topic/CTime::GetSecond.md)|devuelve el segundo representado por el objeto de `CTime` .|  
|[CTime::GetTime](../Topic/CTime::GetTime.md)|Devuelve un valor de **\_\_time64\_t** para el objeto especificado de `CTime` .|  
|[CTime::GetYear](../Topic/CTime::GetYear.md)|Devuelve el año representado por el objeto de `CTime` .|  
|[CTime::Serialize64](../Topic/CTime::Serialize64.md)|Serializa los datos a o desde un archivo.|  
  
### Operadores  
  
|||  
|-|-|  
|[operador \+ –](../Topic/CTime::operator%20+,%20-.md)|estos operadores agregan y restan `CTimeSpan` y los objetos de `CTime` .|  
|[operador \+\=, – \=](../Topic/CTime::operator%20+=,%20-=.md)|Estos operadores agregan y restar un objeto de `CTimeSpan` a y desde este objeto de `CTime` .|  
|[operador \=](../Topic/CTime::operator%20=.md)|el operador de asignación.|  
|[operator \=\=, \<, etc..](../Topic/CTime%20Comparison%20Operators.md)|operadores de comparación.|  
  
## Comentarios  
 `CTime` no tiene una clase base.  
  
 los valores de`CTime` se basan el la hora universal coordinada \(UTC\), que es equivalente a la hora universal coordinada \(hora media de Greenwich o, GMT\).  Vea [Administración del tiempo](../../c-runtime-library/time-management.md) para obtener información sobre cómo se determina la zona horaria.  
  
 Cuando se crea un objeto de `CTime` , establezca el parámetro de `nDST` en 0 para indicar que la hora estándar está vigente, o un valor mayor que 0 para indicar que el tiempo de guardar de luz está vigente, o un valor menor que cero para obtener el cálculo del código de la biblioteca en tiempo de ejecución de C si la hora estándar o tiempo de guardar de luz está vigente.  `tm_isdst` es un campo obligatorio.  Si no establece, su valor es indefinido y el valor devuelto de [mktime](../../c-runtime-library/reference/mktime-mktime32-mktime64.md) es imprevisible.  Si los puntos de `timeptr` a una estructura de TM devuelta por una llamada anterior a [asctime\_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md), a [\_gmtime\_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md), o a [localtime\_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md), el campo de `tm_isdst` contienen el valor correcto.  
  
 Una clase complementaria, [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md), representa un intervalo de tiempo.  
  
 Las clases de `CTime` y de `CTimeSpan` no están diseñados para la derivación.  Porque no hay funciones virtuales, el tamaño de `CTime` y objetos de `CTimeSpan` es 8 bytes.  La mayoría de las funciones miembro inline.  
  
> [!NOTE]
>  La fecha límite superior es 12\/31\/3000.  El límite inferior es 1\/1\/1970 12:00: GMT OF 00.  
  
 Para obtener más información sobre cómo utilizar `CTime`, vea los artículos [fecha y hora](../../atl-mfc-shared/date-and-time.md), y [administración de tiempo](../../c-runtime-library/time-management.md) en la referencia de la biblioteca en tiempo de ejecución.  
  
> [!NOTE]
>  La estructura de `CTime` modificada de MFC 7,1 a MFC 8,0.  Si se serializa una estructura de `CTime` mediante `operator <<` en MFC 8,0 o una versión posterior, el archivo resultante no será legible en versiones anteriores de MFC.  
  
## Requisitos  
 **encabezado:** atltime.h  
  
## Vea también  
 [asctime\_s, \_wasctime\_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [\_ftime\_s, \_ftime32\_s, \_ftime64\_s](../../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)   
 [gmtime\_s, \_gmtime32\_s, \_gmtime64\_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime\_s, \_localtime32\_s, \_localtime64\_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [strftime, wcsftime, \_strftime\_l, \_wcsftime\_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)   
 [time, \_time32, \_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [CTimeSpan Class](../../atl-mfc-shared/reference/ctimespan-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [ATL\/MFC Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)