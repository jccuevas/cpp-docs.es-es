---
title: 'Hora actual: Clases de propósito General'
ms.date: 11/04/2016
helpviewer_keywords:
- time, setting current
- current time, CTime object
- procedures, getting current time
- initializing objects, with the current time
- time, getting current
ms.assetid: c39e6775-6a92-4b27-95a7-5c86ed371d8a
ms.openlocfilehash: e883a47243feb7ad1555748ffdda9b8ae9594644
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539261"
---
# <a name="current-time-general-purpose-classes"></a>Hora actual: Clases de propósito General

El siguiente procedimiento muestra cómo crear un `CTime` objeto e inicializarlo con la hora actual.

### <a name="to-get-the-current-time"></a>Para obtener la hora actual

1. Asignar un `CTime` objeto, como se indica a continuación:

   [!code-cpp[NVC_ATLMFC_Utilities#171](../atl-mfc-shared/codesnippet/cpp/current-time-general-purpose-classes_1.cpp)]

   > [!NOTE]
   > Sin inicializar `CTime` objetos no se inicializan con una hora válida.

1. Llame a la `CTime::GetCurrentTime` función para obtener la hora actual del sistema operativo. Esta función devuelve un `CTime` objeto que puede usarse para establecer el valor de `CTime`, como sigue:

   [!code-cpp[NVC_ATLMFC_Utilities#172](../atl-mfc-shared/codesnippet/cpp/current-time-general-purpose-classes_2.cpp)]

   Puesto que `GetCurrentTime` es una función miembro estática desde la `CTime` (clase), debe calificar su nombre con el nombre de la clase y el operador de resolución de ámbito (`::`), `CTime::GetCurrentTime()`.

Por supuesto, los dos pasos descritos anteriormente podrían combinarse en una única instrucción del programa como sigue:

[!code-cpp[NVC_ATLMFC_Utilities#173](../atl-mfc-shared/codesnippet/cpp/current-time-general-purpose-classes_3.cpp)]
