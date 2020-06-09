---
title: Clases de aplicación y de compatibilidad con subprocesos
ms.date: 11/04/2016
f1_keywords:
- vc.classes.support
helpviewer_keywords:
- application objects [MFC], thread support classes
- lock classes [MFC]
- thread support classes [MFC]
- threading [MFC]
- synchronization classes [MFC], multithreading
- application support classes [MFC]
ms.assetid: 3c1d14fd-c35c-48f1-86ce-1e0f9a32c36d
ms.openlocfilehash: 7e64cc50a121f457b7e32e0ed549db2fa9950843
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619447"
---
# <a name="application-and-thread-support-classes"></a>Clases de aplicación y de compatibilidad con subprocesos

Cada aplicación tiene solo un objeto de aplicación; Este objeto coordina otros objetos en el programa en ejecución y se deriva de `CWinApp` .

La biblioteca MFC (Microsoft Foundation Class) admite varios subprocesos de ejecución dentro de una aplicación. Todas las aplicaciones deben tener al menos un subproceso; el subproceso que usa el `CWinApp` objeto es este subproceso principal.

`CWinThread`encapsula una parte de las capacidades de subproceso del sistema operativo. Para facilitar el uso de varios subprocesos, MFC también proporciona clases de objetos de sincronización para proporcionar una interfaz de C++ a los objetos de sincronización de Win32.

## <a name="application-and-thread-classes"></a>Clases de aplicación y subproceso

[CWinApp](reference/cwinapp-class.md)<br/>
Encapsula el código para inicializar, ejecutar y finalizar la aplicación. Derivará el objeto de aplicación de esta clase.

[CWinThread](reference/cwinthread-class.md)<br/>
La clase base para todos los subprocesos. Use directamente o derive una clase de `CWinThread` si el subproceso realiza funciones de la interfaz de usuario. La clase `CWinApp` se deriva de la clase `CWinThread`.

## <a name="synchronization-object-classes"></a>Clases de objetos de sincronización

[CSyncObject](reference/csyncobject-class.md)<br/>
Clase base de las clases de objeto de sincronización.

[CCriticalSection](reference/ccriticalsection-class.md)<br/>
Una clase de sincronización que permite que solo un subproceso de un único proceso tenga acceso a un objeto.

[CSemaphore](reference/csemaphore-class.md)<br/>
Una clase de sincronización que permite entre uno y un número máximo especificado de accesos simultáneos a un objeto.

[CMutex](reference/cmutex-class.md)<br/>
Una clase de sincronización que permite que solo un subproceso dentro de cualquier número de procesos tenga acceso a un objeto.

[CEvent](reference/cevent-class.md)<br/>
Una clase de sincronización que notifica A una aplicación cuando se ha producido un evento.

[CSingleLock](reference/csinglelock-class.md)<br/>
Se utiliza en funciones miembro de clases seguras para subprocesos para bloquear en un objeto de sincronización.

[CMultiLock](reference/cmultilock-class.md)<br/>
Se usa en funciones miembro de clases seguras para subprocesos para bloquear en uno o varios objetos de sincronización de una matriz de objetos de sincronización.

## <a name="related-classes"></a>Clases relacionadas

[CCommandLineInfo](reference/ccommandlineinfo-class.md)<br/>
Analiza la línea de comandos con la que se inició el programa.

[CWaitCursor](reference/cwaitcursor-class.md)<br/>
Coloca un cursor de espera en la pantalla. Se usa durante las operaciones largas.

[CDockState](reference/cdockstate-class.md)<br/>
Controla el almacenamiento persistente de datos de estado de acoplamiento para las barras de control.

[CRecentFileList](reference/crecentfilelist-class.md)<br/>
Mantiene la lista de archivos usados más recientemente (MRU).

## <a name="see-also"></a>Consulte también

[Información general de clases](class-library-overview.md)
