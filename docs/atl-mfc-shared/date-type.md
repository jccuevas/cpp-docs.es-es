---
title: Tipo de FECHA
ms.date: 11/04/2016
f1_keywords:
- DATE
helpviewer_keywords:
- Date data type, implementing
- Date data type
- DATE type
- Date data type, about Date data type
- MFC, date and time
- hour values representation
ms.assetid: 695853ed-b614-4575-b793-b8c287372038
ms.openlocfilehash: 6fd9fde83474ff4f439c0dd3989d4dc35fe1241a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317922"
---
# <a name="date-type"></a>Tipo de FECHA

El tipo DATE se implementa mediante un número de punto flotante de 8 bytes. Los días están representados por incrementos de números enteros a partir del 30 de diciembre de 1899, medianoche como hora cero. Los valores de hora se expresan como el valor absoluto de la parte fraccionaria del número. En la tabla siguiente se ilustran varias fechas junto con su equivalente numérico de tipo DATE:

|Fecha y hora|Representación|
|-------------------|--------------------|
|30 de diciembre de 1899, medianoche|0.00|
|1 de enero de 1900, medianoche|2.00|
|4 de enero de 1900, medianoche|5.00|
|4 de enero de 1900, 6 a.m.|5.25|
|4 de enero de 1900, mediodía|5.50|
|4 de enero de 1900, 9 P.M.|5.875|

El tipo de fecha FECHA, así como la `COleDateTime` clase, representa fechas y horas como una línea numérica clásica. La `COleDateTime` clase contiene varios métodos para manipular valores DATE, incluida la conversión a y desde otros formatos de fecha comunes.

Los siguientes puntos deben tenerse en cuenta al trabajar con estos formatos de fecha y hora en Automation:

- Las fechas se especifican en la hora local; la sincronización debe realizarse manualmente cuando se trabaja con fechas en diferentes zonas horarias.

- Los tipos de fecha no representan el horario de verano.

- El cronograma de fecha sin escalas para los valores de fecha inferiores a 0 (antes del 30 de diciembre de 1899). Esto se debe a que la parte de número entero del valor de fecha se trata como firmada, mientras que la parte fraccionaria se trata como sin signo. En otras palabras, la parte de número entero del valor de fecha puede ser positiva o negativa, mientras que la parte fraccionaria del valor de fecha siempre se agrega a la fecha lógica general. En la tabla siguiente se muestran algunos ejemplos:

|Fecha y hora|Representación|
|-------------------|--------------------|
|27 de diciembre de 1899, medianoche|-3.00|
|28 de diciembre de 1899, mediodía|-2.50|
|28 de diciembre de 1899, medianoche|-2.00|
|29 de diciembre de 1899, medianoche|-1.00|
|30 de diciembre de 1899, 6 P.M.|-0.75|
|30 de diciembre de 1899, mediodía|-0.50|
|30 de diciembre de 1899, 6 a.m.|-0.25|
|30 de diciembre de 1899, medianoche|0.00|
|30 de diciembre de 1899, 6 a.m.|0,25|
|30 de diciembre de 1899, mediodía|0.50|
|30 de diciembre de 1899, 6 P.M.|0.75|
|31 de diciembre de 1899, medianoche|1.00|
|1 de enero de 1900, medianoche|2.00|
|1 de enero de 1900, mediodía|2.50|
|2 de enero de 1900, medianoche|3.00|

> [!CAUTION]
> Tenga en cuenta que debido a que las 6:00 am siempre están representadas por un valor fraccionario 0,25 independientemente de si el entero que representa el día es positivo (después del 30 de diciembre de 1899) o negativo (antes del 30 de diciembre de 1899), una comparación de punto flotante simple ordenaría erróneamente cualquier FECHA que represente a las 6:00 a.m. de un día anterior al 12/30/1899 a *partir* de la fecha que representa a las 7:00 a.m. ese mismo día.

Puede encontrar más información sobre `COleDateTime` los problemas relacionados con la FECHA y los tipos en [COleDateTime Clase](../atl-mfc-shared/reference/coledatetime-class.md) y [Fecha y hora: Soporte de automatización](../atl-mfc-shared/date-and-time-automation-support.md).

## <a name="see-also"></a>Consulte también

[Fecha y hora](../atl-mfc-shared/date-and-time.md)<br/>
[Clase COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)
