---
title: 'Fecha y hora: Compatibilidad con la base de datos'
ms.date: 11/04/2016
helpviewer_keywords:
- tables [C++]
- dates [C++], database support
- COleDateTime class, database programming
- time [C++], database support
- database tables [C++], date/time data
- tables [C++], date/time data
- databases [C++], date/time data
- COleDateTimeSpan class, database programming
ms.assetid: 4a57a1bb-fad5-4b70-b32c-42ad75c710c8
ms.openlocfilehash: 5e15770558e011fd41b29135f7efbefc2ad8c434
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750225"
---
# <a name="date-and-time-database-support"></a>Fecha y hora: Compatibilidad con la base de datos

A partir de la versión 4.0, MFC base de datos utiliza programación el [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) y [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md) clases para representar datos de fecha y hora. Estas clases, también se usa en la automatización, se derivan de una clase [COleVariant](../mfc/reference/colevariant-class.md). Proporcionan una mejor compatibilidad para administrar datos de fecha y hora que [CTime](../atl-mfc-shared/reference/ctime-class.md) y [CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md).

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Compatibilidad de automatización de la fecha y la programación de tiempo](../atl-mfc-shared/date-and-time-automation-support.md)

## <a name="see-also"></a>Vea también

[Fecha y hora](../atl-mfc-shared/date-and-time.md)
