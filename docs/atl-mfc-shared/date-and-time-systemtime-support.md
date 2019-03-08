---
title: 'Fecha y hora: Compatibilidad con SYSTEMTIME'
ms.date: 11/04/2016
f1_keywords:
- SYSTEMTIME
helpviewer_keywords:
- system time
- FILETIME structure, with CTime class
- time [C++], formatting
- SYSTEMTIME structure
- dates [C++], MFC
- formatting [C++], time
ms.assetid: 201528e4-2ffa-48fc-af8f-203aa86d942a
ms.openlocfilehash: e4aac4078ce6d75fb1613c158cdf790f2a596a01
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893501"
---
# <a name="date-and-time-systemtime-support"></a>Fecha y hora: Compatibilidad con SYSTEMTIME

El [CTime](../atl-mfc-shared/reference/ctime-class.md) clase tiene constructores que aceptan horas de archivo y sistema de Win32. Si usa objetos `CTime` con estos propósitos, deberá modificar sus correspondientes inicializaciones en consecuencia, tal y como se describe en este artículo.

Para obtener información acerca de la estructura SYSTEMTIME, vea [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime). Para obtener información acerca de la estructura FILETIME, vea [FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime).

Aunque MFC sigue ofreciendo constructores `CTime` que toman argumentos de hora en el estilo de MS-DOS, a partir de la versión 3.0 de MFC, la clase `CTime` también admitirá un constructor que toma una estructura `SYSTEMTIME` de Win32 y otra estructura `FILETIME` de Win32.

Los nuevos constructores `CTime` son:

- CTime (SYSTEMTIME const & `sysTime`);

- CTime (FILETIME const & `fileTime`);

El *fileTime* parámetro es una referencia a un Win32 `FILETIME` estructura, que representa la hora como un valor de 64 bits, un formato más cómodo para almacenarlo internamente que una `SYSTEMTIME` estructura y el formato utilizado por Win32 para representan la hora de creación del archivo.

Si su código contiene un objeto `CTime` inicializado con la hora del sistema, le conviene usar el constructor `SYSTEMTIME` en Win32.

Lo más probable es que no usará `CTime` `FILETIME` inicialización directamente. Si usa un `CFile` objeto para manipular un archivo, [CFile:: GetStatus](../mfc/reference/cfile-class.md#getstatus) recupera la marca de tiempo del archivo por usted a través de un `CTime` objeto inicializado con un `FILETIME` estructura.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Fecha general y la programación de tiempo en MFC](../atl-mfc-shared/date-and-time.md)

- [Compatibilidad de automatización de la fecha y la programación de tiempo](../atl-mfc-shared/date-and-time-automation-support.md)

## <a name="see-also"></a>Vea también

[Fecha y hora](../atl-mfc-shared/date-and-time.md)
