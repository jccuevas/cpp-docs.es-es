---
title: 'Tiempo transcurrido: Clases de automatización | Documentos de Microsoft'
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
- dates, calculating intervals
- elapsed time, calculating in Automation
- Automation classes, elapsed time
- time, elapsed
- intervals, date and time
- calculations, date and time
ms.assetid: 26b34b37-c10e-4b91-82c3-1dc5ffb5361f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c1abf6274137ae67b159ad43612d24020a0d14e9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="elapsed-time-automation-classes"></a>Tiempo transcurrido: Clases de automatización
Este procedimiento muestra cómo calcular la diferencia entre dos `CTime` objetos y obtener un `CTimeSpan` resultado.  
  
#### <a name="to-calculate-elapsed-time"></a>Para calcular el tiempo transcurrido  
  
1.  Cree dos `COleDateTime` objetos.  
  
2.  Establezca uno de los `COleDateTime` objetos a la hora actual.  
  
3.  Realizar algunas tareas que consumen muchos recursos.  
  
4.  Establezca las demás `COleDateTime` objeto a la hora actual.  
  
5.  Tomar la diferencia entre los dos veces.  
  
     [!code-cpp[NVC_ATLMFC_Utilities#178](../atl-mfc-shared/codesnippet/cpp/elapsed-time-automation-classes_1.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Fecha y hora: Compatibilidad de automatización](../atl-mfc-shared/date-and-time-automation-support.md)

