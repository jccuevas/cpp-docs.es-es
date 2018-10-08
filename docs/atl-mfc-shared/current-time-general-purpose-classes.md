---
title: 'Hora actual: Clases de propósito General | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- time, setting current
- current time, CTime object
- procedures, getting current time
- initializing objects, with the current time
- time, getting current
ms.assetid: c39e6775-6a92-4b27-95a7-5c86ed371d8a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9edf381864121d4e3f6c5a2b6cf7c01198368e1e
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860529"
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
