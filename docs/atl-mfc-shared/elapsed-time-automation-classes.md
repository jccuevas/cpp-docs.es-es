---
title: "Tiempo transcurrido: Clases de automatización | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0e4cf7fef17499910d9664ab26fa1b07438e7900
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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

