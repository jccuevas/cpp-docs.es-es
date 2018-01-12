---
title: "Tiempo transcurrido: Clases de propósito general | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords:
- adding dates
- calculating dates and times
- dates, calculating intervals
- elapsed time, calculating
- elapsed time
- time, elapsed
- intervals, date and time
- calculations, date and time
ms.assetid: e5c5d3d2-ce1d-409e-875c-98848434e716
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 51eea60669fb7ad35525d65013ffc8420649349b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="elapsed-time-general-purpose-classes"></a>Tiempo transcurrido: Clases de propósito general
El siguiente procedimiento muestra cómo calcular la diferencia entre dos `CTime` objetos y obtener un `CTimeSpan` resultado.  
  
#### <a name="to-calculate-elapsed-time"></a>Para calcular el tiempo transcurrido  
  
1.  Use la `CTime` y `CTimeSpan` objetos que se va a calcular el tiempo transcurrido, del siguiente modo:  
  
     [!code-cpp[NVC_ATLMFC_Utilities#174](../atl-mfc-shared/codesnippet/cpp/elapsed-time-general-purpose-classes_1.cpp)]  
  
     Una vez que ha calculado `elapsedTime`, puede utilizar las funciones miembro de `CTimeSpan` para extraer los componentes del valor de tiempo transcurrido.  
  
## <a name="see-also"></a>Vea también  
 [Fecha y hora: Clases de propósito general](../atl-mfc-shared/date-and-time-general-purpose-classes.md)

