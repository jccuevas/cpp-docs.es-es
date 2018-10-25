---
title: 'Tiempo transcurrido: Clases de propósito general | Microsoft Docs'
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
ms.openlocfilehash: 54c3061ac0d081d04834ba4a8b7336732d854199
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50055871"
---
# <a name="elapsed-time-general-purpose-classes"></a>Tiempo transcurrido: Clases de propósito general

El siguiente procedimiento muestra cómo calcular la diferencia entre dos `CTime` objetos y obtenga un `CTimeSpan` resultado. Use la `CTime` y `CTimeSpan` objetos que se va a calcular el tiempo transcurrido, como sigue:

   [!code-cpp[NVC_ATLMFC_Utilities#174](../atl-mfc-shared/codesnippet/cpp/elapsed-time-general-purpose-classes_1.cpp)]

Una vez que hayan calculado `elapsedTime`, puede usar las funciones miembro de `CTimeSpan` para extraer los componentes del valor de tiempo transcurrido.

