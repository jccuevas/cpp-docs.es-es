---
title: 'Fecha y hora: compatibilidad con SYSTEMTIME | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- SYSTEMTIME
dev_langs:
- C++
helpviewer_keywords:
- system time
- FILETIME structure, with CTime class
- time [C++], formatting
- SYSTEMTIME structure
- dates [C++], MFC
- formatting [C++], time
ms.assetid: 201528e4-2ffa-48fc-af8f-203aa86d942a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ecbfd517a0fd535a23920ae21d03f1756babc113
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="date-and-time-systemtime-support"></a>Fecha y hora: compatibilidad con SYSTEMTIME
El [CTime](../atl-mfc-shared/reference/ctime-class.md) clase tiene constructores que aceptan horas de archivo y de sistema de Win32. Si usa objetos `CTime` con estos propósitos, deberá modificar sus correspondientes inicializaciones en consecuencia, tal y como se describe en este artículo.  
  
 Para obtener información acerca de la estructura SYSTEMTIME, vea [SYSTEMTIME](../mfc/reference/systemtime-structure1.md). Para obtener información acerca de la estructura FILETIME, vea [FILETIME](../mfc/reference/filetime-structure.md).  
  
 Aunque MFC sigue ofreciendo constructores `CTime` que toman argumentos de hora en el estilo de MS-DOS, a partir de la versión 3.0 de MFC, la clase `CTime` también admitirá un constructor que toma una estructura `SYSTEMTIME` de Win32 y otra estructura `FILETIME` de Win32.  
  
 Los nuevos constructores `CTime` son:  
  
-   CTime (SYSTEMTIME const & `sysTime`);  
  
-   CTime (FILETIME const & `fileTime`);  
  
 El parámetro `fileTime` es una referencia a la estructura `FILETIME` de Win32, que representa la hora como un valor de 64 bits, lo cual constituye un formato más cómodo para almacenarlo internamente que una estructura `SYSTEMTIME` y el formato que Win32 usa para representar la hora de creación de un archivo.  
  
 Si su código contiene un objeto `CTime` inicializado con la hora del sistema, le conviene usar el constructor `SYSTEMTIME` en Win32.  
  
 Lo más probable es que no utilizará `CTime` `FILETIME` inicialización directamente. Si utiliza un `CFile` objeto para manipular un archivo, [CFile:: GetStatus](../mfc/reference/cfile-class.md#getstatus) recupera la marca de tiempo del archivo por medio una `CTime` objeto inicializado con un `FILETIME` estructura.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Fecha general y la programación de tiempo en MFC](../atl-mfc-shared/date-and-time.md)  
  
-   [Compatibilidad de automatización de la fecha y la programación de tiempo](../atl-mfc-shared/date-and-time-automation-support.md)  
  
-   [Clases de propósito general para la fecha y la programación de tiempo](../atl-mfc-shared/date-and-time-general-purpose-classes.md)  
  
## <a name="see-also"></a>Vea también  
 [Fecha y hora](../atl-mfc-shared/date-and-time.md)

