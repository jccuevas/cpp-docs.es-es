---
title: 'Tiempo transcurrido: Clases de propósito general'
ms.date: 11/04/2016
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
ms.openlocfilehash: ebaf77b34411cd55cb3a028bcce9109613b63ed9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50676758"
---
# <a name="elapsed-time-general-purpose-classes"></a>Tiempo transcurrido: Clases de propósito general

El siguiente procedimiento muestra cómo calcular la diferencia entre dos `CTime` objetos y obtenga un `CTimeSpan` resultado. Use la `CTime` y `CTimeSpan` objetos que se va a calcular el tiempo transcurrido, como sigue:

   [!code-cpp[NVC_ATLMFC_Utilities#174](../atl-mfc-shared/codesnippet/cpp/elapsed-time-general-purpose-classes_1.cpp)]

Una vez que hayan calculado `elapsedTime`, puede usar las funciones miembro de `CTimeSpan` para extraer los componentes del valor de tiempo transcurrido.

