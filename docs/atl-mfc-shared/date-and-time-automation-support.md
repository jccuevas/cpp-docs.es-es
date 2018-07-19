---
title: 'Fecha y hora: compatibilidad con automatización | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- adding dates
- calculating dates and times
- formatting [Visual Studio], dates
- dates, Automation support
- elapsed time, calculating in Automation
- COleDateTime class, Automation date/time support
- COleDateTimeSpan class, Automation date/time support
- Automation, date and time support
- formatting [Visual Studio], time
- calculations, date and time
- time [Visual Studio], Automation support
ms.assetid: 6eee94c4-943d-4ffc-bf7c-bdda89337ab0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 915bcd5487f423b6240061a0e85f5554a3224397
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357599"
---
# <a name="date-and-time-automation-support"></a>Fecha y hora: compatibilidad con automatización
En este artículo se describe cómo aprovechar las ventajas de los servicios de biblioteca de clase relacionados con la administración de fecha y hora. Los procedimientos descritos incluyen:  
  
-   [Obtener la hora actual](../atl-mfc-shared/current-time-automation-classes.md)  
  
-   [Calcular el tiempo transcurrido](../atl-mfc-shared/elapsed-time-automation-classes.md)  
  
-   [Aplicar formato a una representación de cadena de una fecha y hora](../atl-mfc-shared/formatting-time-automation-classes.md)  
  
 El [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) clase proporciona una manera de representar la información de fecha y hora. Proporciona una mayor granularidad y un intervalo mayor que el [CTime](../atl-mfc-shared/reference/ctime-class.md) clase. El [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md) clase representa el tiempo transcurrido, como la diferencia entre dos `COleDateTime` objetos.  
  
 El `COleDateTime` y `COleDateTimeSpan` clases están diseñadas para usarse con la `COleVariant` clase usada en la automatización. `COleDateTime` y `COleDateTimeSpan` también son útiles en la programación de la base de datos MFC, pero pueden usarse siempre que lo desee para manipular valores de fecha y hora. Aunque la `COleDateTime` clase tiene un mayor intervalo de valores y granularidad más fina que la `CTime` (clase), requiere más espacio de almacenamiento por cada objeto que `CTime`. Hay también algunas consideraciones especiales cuando se trabaja con subyacente **fecha** tipo. Vea [el tipo de fecha](../atl-mfc-shared/date-type.md) para obtener más detalles sobre la implementación de **fecha**.  
  
 `COleDateTime` objetos se pueden usar para representar fechas comprendidas entre el 1 de enero de 100 y el 31 de diciembre de 9999. `COleDateTime` los objetos son flotantes valores de punto, con una resolución aproximada de 1 milisegundo. `COleDateTime` se basa en el **fecha** tipo de datos, definido en la documentación de MFC bajo [COleDateTime:: operador DATE](../atl-mfc-shared/reference/coledatetime-class.md#operator_date). La implementación real de **fecha** se extiende más allá de estos límites. El `COleDateTime` implementación impone estos límites para facilitar el trabajo con la clase.  
  
 `COleDateTime` no admite fechas del calendario juliano. Se supone que el calendario gregoriano para extender en el tiempo para el 1 de enero de 100.  
  
 `COleDateTime` omite el horario de verano (DST). En el ejemplo de código siguiente se compara dos métodos de cálculo de un intervalo de tiempo que cruza la fecha de cambio de horario de verano: uno utilizando CRT y otro usando `COleDateTime`. Horario de verano cambia, en la mayoría de las configuraciones regionales, en la segunda semana de abril y el tercero en octubre.  
  
 El primer método establece dos `CTime` objetos, *tiempo1* y *al tiempo2*, 5 de abril y 6 de abril respectivamente, utilizando las estructuras de tipo C estándares **tm** y `time_t`. El código muestra *tiempo1* y *al tiempo2* y el intervalo de tiempo entre ellos.  
  
 El segundo método, crea dos `COleDateTime` objetos, `oletime1` y `oletime2`y los establece en las mismas fechas que *tiempo1* y *al tiempo2*. Muestra `oletime1` y `oletime2` y el intervalo de tiempo entre ellos.  
  
 CRT calcula correctamente una diferencia de 23 horas. `COleDateTimeSpan` calcula una diferencia de 24 horas.  
  
 Tenga en cuenta que se utiliza una solución cerca del final del ejemplo para mostrar correctamente la fecha usando `COleDateTime::Format`. Vea el artículo de Knowledge Base "Error: se produce un error en Format para `COleDateTime` y `COleDateTimeSpan`" (Q167338).  
  
 [!code-cpp[NVC_ATLMFC_Utilities#176](../atl-mfc-shared/codesnippet/cpp/date-and-time-automation-support_1.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Fecha y hora](../atl-mfc-shared/date-and-time.md)

