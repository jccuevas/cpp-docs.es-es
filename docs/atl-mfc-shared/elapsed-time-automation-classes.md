---
title: 'Tiempo transcurrido: Clases de automatización'
ms.date: 11/04/2016
helpviewer_keywords:
- adding dates
- calculating dates and times
- dates, calculating intervals
- elapsed time, calculating in Automation
- Automation classes, elapsed time
- time, elapsed
- intervals, date and time
- calculations, date and time
ms.assetid: 26b34b37-c10e-4b91-82c3-1dc5ffb5361f
ms.openlocfilehash: d6a77d57a88166354fcb222c0da09690426108e9
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750054"
---
# <a name="elapsed-time-automation-classes"></a>Tiempo transcurrido: Clases de automatización

Este procedimiento muestra cómo calcular la diferencia entre dos `CTime` objetos y obtenga un `CTimeSpan` resultado.

## <a name="to-calculate-elapsed-time"></a>Para calcular el tiempo transcurrido

1. Cree dos `COleDateTime` objetos.

1. Establezca uno de los `COleDateTime` objetos a la hora actual.

1. Realizar algunas tareas que requieren mucho tiempo.

1. La otra `COleDateTime` objeto a la hora actual.

1. Tomar la diferencia entre las dos horas.

   [!code-cpp[NVC_ATLMFC_Utilities#178](../atl-mfc-shared/codesnippet/cpp/elapsed-time-automation-classes_1.cpp)]

## <a name="see-also"></a>Vea también

[Fecha y hora: Compatibilidad de automatización](../atl-mfc-shared/date-and-time-automation-support.md)
