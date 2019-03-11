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
ms.openlocfilehash: 5990f6f5db0270c8d24ff35b5c9bbea5b24e6ed7
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57742038"
---
# <a name="elapsed-time-general-purpose-classes"></a>Tiempo transcurrido: Clases de propósito general

El siguiente procedimiento muestra cómo calcular la diferencia entre dos `CTime` objetos y obtenga un `CTimeSpan` resultado. Use la `CTime` y `CTimeSpan` objetos que se va a calcular el tiempo transcurrido, como sigue:

   [!code-cpp[NVC_ATLMFC_Utilities#174](../atl-mfc-shared/codesnippet/cpp/elapsed-time-general-purpose-classes_1.cpp)]

Una vez que hayan calculado `elapsedTime`, puede usar las funciones miembro de `CTimeSpan` para extraer los componentes del valor de tiempo transcurrido.
