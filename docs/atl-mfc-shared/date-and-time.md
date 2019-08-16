---
title: Fecha y hora
ms.date: 08/13/2019
helpviewer_keywords:
- time, MFC programming
- time
- MFC, date and time
- dates, MFC
ms.assetid: ecf56dc5-d418-4603-ad3e-af7e205a6403
ms.openlocfilehash: 2a5e6977acfca51b8074399f6f9b3166c8a358bc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491299"
---
# <a name="date-and-time"></a>Fecha y hora

MFC admite varias formas de trabajar con fechas y horas:

- Compatibilidad con el [tipo de datos de fecha](../atl-mfc-shared/date-type.md)de automatización. La fecha admite valores de fecha, hora y fecha u hora. Las clases [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) y [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md) encapsulan esta funcionalidad. Funcionan con la clase [COleVariant](../mfc/reference/colevariant-class.md) mediante la compatibilidad con la automatización.

- Clases de tiempo de uso general. Las clases [ctime](../atl-mfc-shared/reference/ctime-class.md) y [CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md) encapsulan la mayor parte de la funcionalidad asociada a la biblioteca de hora de ANSI estándar, que se declara en el tiempo. C.

- Compatibilidad con el reloj del sistema. Con la versión 3,0 `CTime` de MFC, se ha agregado compatibilidad con para los tipos de datos y `FILETIME` de Win32 `SYSTEMTIME` .

## <a name="date-and-time-automation-support"></a>Fecha y hora: Compatibilidad con automatización

La clase [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) proporciona una manera de representar información de fecha y hora. Proporciona una granularidad más fina y un intervalo mayor que la clase [ctime](../atl-mfc-shared/reference/ctime-class.md) . La clase [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md) representa el tiempo transcurrido, como la diferencia entre dos `COleDateTime` objetos.

Las `COleDateTime` clases `COleDateTimeSpan` y están diseñadas para su uso con `COleVariant` la clase. `COleDateTime`y `COleDateTimeSpan` también son útiles en la programación de bases de datos MFC, pero se pueden usar siempre que desee manipular valores de fecha y hora. Aunque la `COleDateTime` clase tiene un intervalo de valores mayor y una granularidad más fina que `CTime` la clase, requiere más almacenamiento por objeto que `CTime`. También hay algunas consideraciones especiales al trabajar con el tipo de fecha subyacente. Para obtener más información sobre la implementación de DATE, vea [el tipo Date](../atl-mfc-shared/date-type.md).

`COleDateTime`los objetos se pueden usar para representar fechas entre el 1 de enero de 100 y el 31 de diciembre de 9999. `COleDateTime`los objetos son valores de punto flotante, con una resolución aproximada de 1 milisegundo. `COleDateTime`se basa en el tipo de datos DATE, definido en la documentación de MFC en [COleDateTime:: Operator Date](../atl-mfc-shared/reference/coledatetime-class.md#operator_date). La implementación real de DATE se extiende más allá de estos límites. La `COleDateTime` implementación impone estos límites para facilitar el trabajo con la clase.

`COleDateTime`no admite fechas Juliano. Se supone que el calendario gregoriano se extiende hacia atrás en el plazo del 1 de enero de 100.

`COleDateTime`omite el horario de verano (DST). En el ejemplo de código siguiente se comparan dos métodos de cálculo de un intervalo de tiempo que cruza la fecha de cambio de DST: uno que `COleDateTime`usa CRT y el otro mediante.

El primer método establece dos `CTime` objetos, *tiempo1* y *al tiempo2?* , en el 5 de abril y en el 6 de abril, respectivamente, `tm` con `time_t`las estructuras de tipo estándar de C y. El código muestra *tiempo1* y *al tiempo2?* y el intervalo de tiempo entre ellos.

El segundo método crea dos `COleDateTime` objetos, `oletime1` y `oletime2`, y los establece en las mismas fechas que *tiempo1* y *al tiempo2?* . Muestra `oletime1` y`oletime2` y el intervalo de tiempo entre ellos.

CRT calcula correctamente una diferencia de 23 horas. `COleDateTimeSpan`calcula una diferencia de 24 horas.

[!code-cpp[NVC_ATLMFC_Utilities#176](../atl-mfc-shared/codesnippet/cpp/date-and-time-automation-support_1.cpp)]

### <a name="get-the-current-time"></a>Obtener la hora actual

En el siguiente procedimiento se muestra cómo crear `COleDateTime` un objeto e inicializarlo con la hora actual.

#### <a name="to-get-the-current-time"></a>Para obtener la hora actual

1. Crear un objeto `COleDateTime`.

1. Llame a `GetCurrentTime`.

   [!code-cpp[NVC_ATLMFC_Utilities#177](../atl-mfc-shared/codesnippet/cpp/current-time-automation-classes_1.cpp)]

### <a name="calculate-elapsed-time"></a>Calcular el tiempo transcurrido

Este procedimiento muestra cómo calcular la diferencia entre dos `COleDateTime` objetos y obtener un `COleDateTimeSpan` resultado.

#### <a name="to-calculate-elapsed-time"></a>Para calcular el tiempo transcurrido

1. Cree dos `COleDateTime` objetos.

1. Establezca uno de los `COleDateTime` objetos en la hora actual.

1. Realice una tarea que consume mucho tiempo.

1. Establezca el otro `COleDateTime` objeto en la hora actual.

1. Tome la diferencia entre las dos horas.

   [!code-cpp[NVC_ATLMFC_Utilities#178](../atl-mfc-shared/codesnippet/cpp/elapsed-time-automation-classes_1.cpp)]

### <a name="format-a-time"></a>Dar formato a una hora

#### <a name="to-format-a-time"></a>Para dar formato a una hora

Utilice la `Format` función miembro de [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) o [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md) para crear una cadena de caracteres que represente la hora o el tiempo transcurrido.

   [!code-cpp[NVC_ATLMFC_Utilities#179](../atl-mfc-shared/codesnippet/cpp/formatting-time-automation-classes_1.cpp)]

Para obtener más información, vea la clase [COleVariant](../mfc/reference/colevariant-class.md).

## <a name="date-and-time-database-support"></a>Fecha y hora: Compatibilidad con bases de datos

A partir de la versión 4,0, la programación de bases de datos MFC utiliza las clases [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) y [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md) para representar datos de fecha y hora. Estas clases, que también se usan en Automation, se derivan de la clase [COleVariant](../mfc/reference/colevariant-class.md). Proporcionan una mejor compatibilidad para administrar datos de fecha y hora que [ctime](../atl-mfc-shared/reference/ctime-class.md) y [CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md).

## <a name="date-and-time-systemtime-support"></a>Fecha y hora: Compatibilidad con SYSTEMTIME

La clase [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) tiene constructores que aceptan horas del sistema y del archivo de Win32.

La estructura `FILETIME` de Win32 representa el tiempo como un valor de 64 bits. Es un formato más cómodo para el almacenamiento interno que una `SYSTEMTIME` estructura y el formato utilizado por Win32 para representar la hora de creación del archivo. Para obtener información sobre la estructura SYSTEMTIME, vea [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime). Para obtener información acerca de la estructura FILETIME, vea [FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime).

## <a name="see-also"></a>Vea también

[Conceptos](../mfc/mfc-concepts.md)\
[Temas generales de MFC](../mfc/general-mfc-topics.md)
