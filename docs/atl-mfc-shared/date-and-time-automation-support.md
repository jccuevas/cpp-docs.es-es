---
title: 'Fecha y hora: Compatibilidad de automatización'
ms.date: 11/04/2016
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
ms.openlocfilehash: c26534189c7b6f904611e78c5d2d6d0b1d6d7382
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750212"
---
# <a name="date-and-time-automation-support"></a>Fecha y hora: Compatibilidad de automatización

En este artículo se describe cómo aprovechar las ventajas de los servicios de biblioteca de clases relacionadas con la administración de la fecha y hora. Los procedimientos descritos incluyen:

- [Introducción a la hora actual](../atl-mfc-shared/current-time-automation-classes.md)

- [Calcular el tiempo transcurrido](../atl-mfc-shared/elapsed-time-automation-classes.md)

- [Aplicar formato a una representación de cadena de una fecha y hora](../atl-mfc-shared/formatting-time-automation-classes.md)

El [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) clase proporciona una manera de representar la información de fecha y hora. Proporciona una mayor granularidad y un intervalo mayor que el [CTime](../atl-mfc-shared/reference/ctime-class.md) clase. El [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md) clase representa el tiempo transcurrido, como la diferencia entre dos `COleDateTime` objetos.

El `COleDateTime` y `COleDateTimeSpan` clases están diseñadas para usarse con la `COleVariant` clase usada en la automatización. `COleDateTime` y `COleDateTimeSpan` también son útiles en la programación de la base de datos MFC, pero puede usarse siempre que quiera manipular los valores de fecha y hora. Aunque el `COleDateTime` clase tiene un mayor intervalo de valores y la granularidad más fina que las `CTime` (clase), requiere más capacidad de almacenamiento por cada objeto que `CTime`. También hay algunas consideraciones especiales cuando se trabaja con el tipo subyacente de la fecha. Consulte [el tipo de fecha](../atl-mfc-shared/date-type.md) para obtener más detalles sobre la implementación de fecha.

`COleDateTime` objetos se pueden usar para representar las fechas entre el 1 de enero de 100 y el 31 de diciembre de 9999. `COleDateTime` los objetos son flotantes valores de punto, con una resolución aproximado de 1 milisegundo. `COleDateTime` se basa en el tipo de datos DATE, definido en la documentación de MFC bajo [COleDateTime:: operador DATE](../atl-mfc-shared/reference/coledatetime-class.md#operator_date). La implementación real de la fecha se extiende más allá de estos límites. El `COleDateTime` implementación impone estos límites para facilitar el trabajo con la clase.

`COleDateTime` no se admite fechas del calendario juliano. Se supone que el calendario gregoriano para extender en el tiempo para el 1 de enero de 100.

`COleDateTime` omite el horario de verano (DST). El ejemplo de código siguiente compara dos métodos de cálculo de un intervalo de tiempo que cruza la fecha de cambio de horario de verano: uno con CRT y el otro con `COleDateTime`. Horario de verano cambia, en la mayoría de las configuraciones regionales, en la segunda semana de abril y el tercero en octubre.

El primer método establece dos `CTime` objetos, *tiempo1* y *tiempo2*, 5 de abril y 6 de abril, respectivamente, mediante las estructuras de tipo de C estándares `tm` y `time_t`. Muestra el código *tiempo1* y *tiempo2* y el intervalo de tiempo entre ellos.

El segundo método, crea dos `COleDateTime` objetos, `oletime1` y `oletime2`y los establece en las mismas fechas como *tiempo1* y *tiempo2*. Muestra `oletime1` y `oletime2` y el intervalo de tiempo entre ellos.

CRT calcula correctamente una diferencia de 23 horas. `COleDateTimeSpan` calcula una diferencia de 24 horas.

[!code-cpp[NVC_ATLMFC_Utilities#176](../atl-mfc-shared/codesnippet/cpp/date-and-time-automation-support_1.cpp)]

## <a name="see-also"></a>Vea también

[Fecha y hora](../atl-mfc-shared/date-and-time.md)
