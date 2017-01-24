---
title: "Fecha y hora: compatibilidad con SYSTEMTIME | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "SYSTEMTIME"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "hora del sistema"
  - "Estructura FILETIME, con la clase CTime"
  - "formato de hora [C++]"
  - "SYSTEMTIME (estructura)"
  - "fechas [C++], MFC"
  - "hora, aplicar formato [C++]"
ms.assetid: 201528e4-2ffa-48fc-af8f-203aa86d942a
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Fecha y hora: compatibilidad con SYSTEMTIME
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El [CTime](../atl-mfc-shared/reference/ctime-class.md) clase tiene constructores que aceptan horas del sistema y archivos de Win32. Si usa objetos `CTime` con estos propósitos, deberá modificar sus correspondientes inicializaciones en consecuencia, tal y como se describe en este artículo.  
  
 Para obtener información acerca de la estructura SYSTEMTIME, vea [SYSTEMTIME](../mfc/reference/systemtime-structure1.md). Para obtener información sobre la estructura FILETIME, vea [FILETIME](../mfc/reference/filetime-structure.md).  
  
 Aunque MFC sigue ofreciendo constructores `CTime` que toman argumentos de hora en el estilo de MS-DOS, a partir de la versión 3.0 de MFC, la clase `CTime` también admitirá un constructor que toma una estructura `SYSTEMTIME` de Win32 y otra estructura `FILETIME` de Win32.  
  
 Los nuevos constructores `CTime` son:  
  
-   CTime (const SYSTEMTIME & `sysTime`);  
  
-   CTime (const FILETIME & `fileTime`);  
  
 El parámetro `fileTime` es una referencia a la estructura `FILETIME` de Win32, que representa la hora como un valor de 64 bits, lo cual constituye un formato más cómodo para almacenarlo internamente que una estructura `SYSTEMTIME` y el formato que Win32 usa para representar la hora de creación de un archivo.  
  
 Si su código contiene un objeto `CTime` inicializado con la hora del sistema, le conviene usar el constructor `SYSTEMTIME` en Win32.  
  
 Probablemente no utilizará `CTime` `FILETIME` inicialización directamente. Si utiliza un `CFile` objeto para manipular un archivo [CFile:: GetStatus](../mfc/reference/cfile-class.md#getstatus) recupera la marca de tiempo del archivo por medio una `CTime` objeto inicializado con un `FILETIME` estructura.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre  
  
-   [General programación de fecha y hora en MFC](../atl-mfc-shared/date-and-time.md)  
  
-   [Compatibilidad de automatización de la programación de fecha y hora](../atl-mfc-shared/date-and-time-automation-support.md)  
  
-   [Clases de propósito general para la programación de fecha y hora](../atl-mfc-shared/date-and-time-general-purpose-classes.md)  
  
## <a name="see-also"></a>Vea también  
 [Fecha y hora](../atl-mfc-shared/date-and-time.md)

