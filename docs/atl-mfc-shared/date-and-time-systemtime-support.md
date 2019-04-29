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
ms.openlocfilehash: be8462858585a5530f360dae97e155b4967239b0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62236416"
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
