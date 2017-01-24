---
title: "Date and Time: Automation Support | Microsoft Docs"
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
  - "adding dates"
  - "automatización, date and time support"
  - "calculating dates and times"
  - "cálculos, fecha y hora"
  - "COleDateTime class, Automation date/time support"
  - "COleDateTimeSpan class, Automation date/time support"
  - "fechas, Automation support"
  - "tiempo transcurrido, calculating in Automation"
  - "dar formato [Visual Studio], fechas"
  - "dar formato [Visual Studio], hora"
  - "horas [Visual Studio], Automation support"
ms.assetid: 6eee94c4-943d-4ffc-bf7c-bdda89337ab0
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Date and Time: Automation Support
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se describe cómo aprovechar los servicios de la biblioteca de clases relacionados hasta la fecha y la administración de tiempo.  Incluyen descrita procedimientos:  
  
-   [obtener la hora actual](../atl-mfc-shared/current-time-automation-classes.md)  
  
-   [Tiempo transcurrido](../atl-mfc-shared/elapsed-time-automation-classes.md)  
  
-   [Dar formato a una representación de cadena de una fecha o una hora](../atl-mfc-shared/formatting-time-automation-classes.md)  
  
 La clase de [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) proporciona una manera de representar la información de fecha y hora.  Proporciona una granularidad más adecuada y un intervalo mayor que la clase de [CTime](../atl-mfc-shared/reference/ctime-class.md) .  La clase de [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md) representa el tiempo transcurrido, como la diferencia entre dos objetos de `COleDateTime` .  
  
 Las clases de `COleDateTime` y de `COleDateTimeSpan` están diseñados para su uso con la clase de `COleVariant` utilizada en la automatización.  `COleDateTime` y `COleDateTimeSpan` también resultan útiles en programación de base de datos de MFC, pero pueden utilizar siempre que desee para manipular valores de fecha y hora.  Aunque la clase de `COleDateTime` tiene un intervalo mayor de valores y una granularidad más fina que la clase de `CTime` , necesita más almacenamiento por objeto que `CTime`.  También hay consideraciones especiales al ejecutar el tipo subyacente de **DATE** .  Vea [El tipo de la DATE](../atl-mfc-shared/date-type.md) para obtener información más detallada sobre la implementación de **DATE**.  
  
 los objetos de`COleDateTime` se pueden utilizar para representar fechas entre el 1 de enero, 100, y el 31 de diciembre, 9999.  los objetos de`COleDateTime` son valores de punto flotante, con una resolución aproximada de 1 milisegundos.  `COleDateTime` se basa en el tipo de datos **DATE** , definido en la documentación de MFC en [COleDateTime:: DATE de operador](../Topic/COleDateTime::operator%20DATE.md).  La implementación real de **DATE** se extiende más allá de ellos limitada.  La implementación de `COleDateTime` impone estos límites para facilitar el trabajo con la clase.  
  
 `COleDateTime` no admite fechas juliano.  El calendario gregoriano se supone para extender vuelve a tiempo 1 de enero, 100.  
  
 `COleDateTime` omite el horario de \(DST\) verano.  El ejemplo de código siguiente compara dos métodos de calcular una duración que cruce la fecha del intercambio de DST: uno utilizando CRT, y mediante `COleDateTime`.  cambios de DST, en la mayoría de las configuraciones regionales, en la segunda semana en abril y el tercero en octubre.  
  
 El primer método establece dos objetos de `CTime` , *time1* y *time2*, el 5 de abril y 6 de abril respectivamente, con las estructuras estándar **TM** y `time_t`de Tipo C.  El código muestra *time1* y *time2* y la duración entre ellos.  
  
 El segundo método crea dos objetos, `oletime1` y `oletime2`de `COleDateTime` , y los establece en las mismas fechas que *time1* y *time2*.  Muestra `oletime1` y `oletime2` y la duración entre ellos.  
  
 CRT correctamente calcula una diferencia de 23 horas.  `COleDateTimeSpan` calcula una diferencia de 24 horas.  
  
 Observe que una solución alternativa se utiliza cerca del final del ejemplo para mostrar la fecha correctamente mediante `COleDateTime::Format`.  Vea el artículo de Knowledge Base “ENTRAR ERRORES OF FUNCIONAMIENTO: Dé formato \(“%D”\) falla en `COleDateTime` y `COleDateTimeSpan`” \(Q167338\).  
  
 [!code-cpp[NVC_ATLMFC_Utilities#176](../atl-mfc-shared/codesnippet/CPP/date-and-time-automation-support_1.cpp)]  
  
## Vea también  
 [Date and Time](../atl-mfc-shared/date-and-time.md)