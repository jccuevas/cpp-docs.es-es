---
title: 'Tiempo transcurrido: Clases de propósito general | Documentos de Microsoft'
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
- elapsed time, calculating
- elapsed time
- time, elapsed
- intervals, date and time
- calculations, date and time
ms.assetid: e5c5d3d2-ce1d-409e-875c-98848434e716
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ff7ef11bb20124a05e2e85c408ce27de8f982546
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32354271"
---
# <a name="elapsed-time-general-purpose-classes"></a>Tiempo transcurrido: Clases de propósito general
El siguiente procedimiento muestra cómo calcular la diferencia entre dos `CTime` objetos y obtener un `CTimeSpan` resultado.  
  
#### <a name="to-calculate-elapsed-time"></a>Para calcular el tiempo transcurrido  
  
1.  Use la `CTime` y `CTimeSpan` objetos que se va a calcular el tiempo transcurrido, del siguiente modo:  
  
     [!code-cpp[NVC_ATLMFC_Utilities#174](../atl-mfc-shared/codesnippet/cpp/elapsed-time-general-purpose-classes_1.cpp)]  
  
     Una vez que ha calculado `elapsedTime`, puede utilizar las funciones miembro de `CTimeSpan` para extraer los componentes del valor de tiempo transcurrido.  
  
## <a name="see-also"></a>Vea también  
 [Fecha y hora: Clases de propósito general](../atl-mfc-shared/date-and-time-general-purpose-classes.md)

