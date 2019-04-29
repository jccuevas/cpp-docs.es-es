---
title: 'Dar formato a valores de tiempo: Clases de propósito general'
ms.date: 11/04/2016
helpviewer_keywords:
- dates, calculating intervals
- elapsed time, string representation
- time [C++], formatting
- formatting [C++], time
ms.assetid: 7fcfee24-f874-4a4d-95b3-adc19a0f2df0
ms.openlocfilehash: bab93638d81e8e4e5d6f7ce71bf6a3180fa7f7e5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62236405"
---
# <a name="formatting-time-values-general-purpose-classes"></a>Dar formato a valores de tiempo: Clases de propósito general

El siguiente procedimiento muestra cómo dar formato a valores de tiempo.

#### <a name="to-format-a-string-representation-of-a-time-or-elapsed-time"></a>Para dar formato a una representación de cadena de una hora o el tiempo transcurrido

Use la `Format` función miembro desde el [CTime](../atl-mfc-shared/reference/ctime-class.md) o [CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md) las clases para crear un carácter de representación de cadena de la hora o el tiempo transcurrido, tal como se muestra en el ejemplo siguiente.

   [!code-cpp[NVC_ATLMFC_Utilities#175](../atl-mfc-shared/codesnippet/cpp/formatting-time-values-general-purpose-classes_1.cpp)]

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Fecha general y la programación de tiempo en MFC](../atl-mfc-shared/date-and-time.md)

- [Trabajar con SYSTEMTIME](../atl-mfc-shared/date-and-time-systemtime-support.md)

- [Compatibilidad de automatización de la fecha y la programación de tiempo](../atl-mfc-shared/date-and-time-automation-support.md)
