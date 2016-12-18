---
title: "COleDateTime Class | Microsoft Docs"
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
  - "COleDateTime"
  - "ATL.COleDateTime"
  - "ATL::COleDateTime"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleDateTime class"
  - "Date (tipo de datos), MFC encapsulation of"
  - "fechas, handling in MFC"
  - "shared classes, COleDateTime"
  - "hora, handling in MFC"
  - "time-only values"
ms.assetid: e718f294-16ec-4649-88b6-a4dbae5178fb
caps.latest.revision: 34
caps.handback.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleDateTime Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Encapsula el tipo de datos `DATE` que se utiliza en la automatización OLE.  
  
## Sintaxis  
  
```  
class COleDateTime  
```  
  
## Members  
  
### Constructores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[COleDateTime::COleDateTime](../Topic/COleDateTime::COleDateTime.md)|Crea un objeto `COleDateTime`.|  
  
### Métodos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[COleDateTime::Format](../Topic/COleDateTime::Format.md)|Genera una representación de cadena con formato de un objeto `COleDateTime` .|  
|[COleDateTime::GetAsDBTIMESTAMP](../Topic/COleDateTime::GetAsDBTIMESTAMP.md)|Llame a este método para obtener el tiempo en el objeto `COleDateTime` como estructura de datos **DBTIMESTAMP** .|  
|[COleDateTime::GetAsSystemTime](../Topic/COleDateTime::GetAsSystemTime.md)|Llame a este método para obtener el tiempo en el objeto `COleDateTime` como estructura de datos [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) .|  
|[COleDateTime::GetAsUDATE](../Topic/COleDateTime::GetAsUDATE.md)|Llame a este método para obtener el tiempo en `COleDateTime` como estructura de datos **UDATE** .|  
|[COleDateTime::GetCurrentTime](../Topic/COleDateTime::GetCurrentTime.md)|Crea un objeto `COleDateTime` que representa la hora actual \(función miembro estática\).|  
|[COleDateTime::GetDay](../Topic/COleDateTime::GetDay.md)|Devuelve el día que este objeto `COleDateTime` representa \(1 – 31\).|  
|[COleDateTime::GetDayOfWeek](../Topic/COleDateTime::GetDayOfWeek.md)|Devuelve el día de la semana que este objeto `COleDateTime` representa \(domingo \= 1\).|  
|[COleDateTime::GetDayOfYear](../Topic/COleDateTime::GetDayOfYear.md)|Devuelve el día del año que este objeto `COleDateTime` representa \(1 de enero \= 1\).|  
|[COleDateTime::GetHour](../Topic/COleDateTime::GetHour.md)|Devuelve la hora que este objeto `COleDateTime` representa \(0 – 23\).|  
|[COleDateTime::GetMinute](../Topic/COleDateTime::GetMinute.md)|Devuelve el minuto que este objeto `COleDateTime` representa \(0 – 59\).|  
|[COleDateTime::GetMonth](../Topic/COleDateTime::GetMonth.md)|Devuelve el mes que este objeto `COleDateTime` representa \(1 – 12\).|  
|[COleDateTime::GetSecond](../Topic/COleDateTime::GetSecond.md)|Devuelve el segundo este objeto `COleDateTime` representa \(0 – 59\).|  
|[COleDateTime::GetStatus](../Topic/COleDateTime::GetStatus.md)|Obtiene el estado \(validez\) de este objeto `COleDateTime` .|  
|[COleDateTime::GetYear](../Topic/COleDateTime::GetYear.md)|Devuelve el año que este objeto `COleDateTime` representa.|  
|[COleDateTime::ParseDateTime](../Topic/COleDateTime::ParseDateTime.md)|Lee un valor de fecha u hora de una cadena y establece el valor `COleDateTime`.|  
|[COleDateTime::SetDate](../Topic/COleDateTime::SetDate.md)|Establece el valor de este objeto `COleDateTime` al valor especificado de la fecha \(sólo.|  
|[COleDateTime::SetDateTime](../Topic/COleDateTime::SetDateTime.md)|Establece el valor de este objeto `COleDateTime` a fecha y el valor de tiempo especificados.|  
|[COleDateTime::SetStatus](../Topic/COleDateTime::SetStatus.md)|Establece el estado \(validez\) de este objeto `COleDateTime` .|  
|[COleDateTime::SetTime](../Topic/COleDateTime::SetTime.md)|Establece el valor de este objeto `COleDateTime` al valor especificado de Tiempo \- únicamente.|  
  
### Operadores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[\=\= De COleDateTime::operator, COleDateTime::operator \<, etc..](../Topic/COleDateTime%20Relational%20Operators.md)|Compara dos valores `COleDateTime` .|  
|[COleDateTime::operator \+, COleDateTime::operator \-](../Topic/COleDateTime::operator%20+,%20-.md)|Agregue y reste los valores `COleDateTime` .|  
|[COleDateTime::operator \+\=, COleDateTime::operator \- \=](../Topic/COleDateTime::operator%20+=,%20-=.md)|Agregue y restar un valor `COleDateTime` de este objeto `COleDateTime` .|  
|[COleDateTime::operator \=](../Topic/COleDateTime::operator%20=.md)|Copia un valor `COleDateTime` .|  
|[DATE de COleDateTime::operator, COleDateTime::operator Date\*](../Topic/COleDateTime::operator%20DATE.md)|Convierte un valor `COleDateTime` en `DATE` o `DATE*`.|  
  
### Miembros de datos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[COleDateTime::m\_dt](../Topic/COleDateTime::m_dt.md)|Contiene **fecha** subyacente para este objeto `COleDateTime` .|  
|[COleDateTime::m\_status](../Topic/COleDateTime::m_status.md)|Contiene el estado de este objeto `COleDateTime` .|  
  
## Comentarios  
 `COleDateTime` no tiene una clase base.  
  
 Es uno de los tipos posibles para el tipo de datos [VARIANT](http://msdn.microsoft.com/es-es/e305240e-9e11-4006-98cc-26f4932d2118) de automatización OLE.  Un valor `COleDateTime` representa un valor absoluto de fecha y hora.  
  
 Implementan el tipo `DATE` como valor de punto flotante.  Los días se miden a partir del 30 de diciembre de 1899, en la medianoche.  La tabla siguiente muestra algunas fechas y sus valores asociados:  
  
|Fecha|Valor|  
|-----------|-----------|  
|29 de diciembre de 1899, Medianoche|\-1.0|  
|29 de diciembre de 1899, 6 Mañanas|\-1.25|  
|30 de diciembre de 1899, Medianoche|0.0|  
|31 de diciembre de 1899, Medianoche|1.0|  
|1 de enero de 1900, 6..|2.25|  
  
> [!CAUTION]
>  La nota en la tabla anterior que aunque los valores del día dejen de ser negativos antes de medianoche el 30 de diciembre de 1899, valores de hora no.  Por ejemplo, las 6:00 se representa siempre por un valor fraccionario 0,25 independientemente de si el entero que representa el día es positivo \(después del 30 de diciembre de 1899\) o negativa \(antes del 30 de diciembre de 1899\).  Esto significa que una comparación simple de punto flotante clasificaría erróneamente `COleDateTime` que representa las 6:00 en 12\/29\/1899 como **later** que un 7:00 de representación en el mismo día.  
  
 La clase `COleDateTime` controla las fechas a partir del 1 de enero, 100, hasta el 31 de diciembre, 9999.  La clase `COleDateTime` utiliza el calendario gregoriano; no admite las fechas juliano.  `COleDateTime` omite el horario de verano.  \(Vea [Fecha y hora: Compatibilidad de automatización](../../atl-mfc-shared/date-and-time-automation-support.md).\)  
  
> [!NOTE]
>  Puede usar el formato `%y` para recuperar un año de dos dígitos sólo por fechas que empieza en 1900.  Si utiliza el formato `%y` en una fecha antes de 1900, el código genera un error ASSERT.  
  
 Utilizan este tipo también para representar valores de fecha \- solo o de Tiempo \- únicamente.  Por convención, la fecha 0 \(30 de diciembre de 1899\) se utiliza para los valores y las 00:00 de tiempo \(medianoche\) de Tiempo \- sólo se utiliza para valores de fecha \- únicamente.  
  
 Si crea un objeto `COleDateTime` mediante una fecha menor que 100, se acepta la fecha, pero las llamadas subsiguientes a `GetYear`, `GetMonth`, `GetDay`, `GetHour`, `GetMinute`, y el error y devuelva \-1 `GetSecond` .  Previamente, puede usar las fechas de dos dígitos, pero las fechas deben ser 100 o más grandes en MFC 4,2 y posterior.  
  
 Para evitar problemas, especifique una fecha de cuatro dígitos.  Por ejemplo:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#1](../../atl-mfc-shared/codesnippet/CPP/coledatetime-class_1.cpp)]  
  
 Las operaciones aritméticas básicas por los valores `COleDateTime` utilizan la clase [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)complementarias.  Los valores de`COleDateTimeSpan` definen un intervalo de tiempo.  La relación entre estas clases es similar a la que está entre [CTime](../../atl-mfc-shared/reference/ctime-class.md) y [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md).  
  
 Para obtener más información sobre las clases `COleDateTime` y `COleDateTimeSpan` , vea el artículo [Fecha y hora: Compatibilidad de automatización](../../atl-mfc-shared/date-and-time-automation-support.md).  
  
## Requisitos  
 **Encabezado:** ATLComTime.h  
  
## Vea también  
 [COleVariant Class](../../mfc/reference/colevariant-class.md)   
 [CTime Class](../../atl-mfc-shared/reference/ctime-class.md)   
 [CTimeSpan Class](../../atl-mfc-shared/reference/ctimespan-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [ATL\/MFC Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)