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
ms.openlocfilehash: 667725a60fb0c907a9c2d017674f9d097d1f4946
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394681"
---
# <a name="application-and-thread-support-classes"></a>Clases de aplicación y de compatibilidad con subprocesos

Cada aplicación tiene solo un objeto de aplicación; Este objeto coordina otros objetos en el programa en ejecución y se deriva de `CWinApp`.

La biblioteca Microsoft Foundation Class (MFC) es compatible con varios subprocesos de ejecución dentro de una aplicación. Todas las aplicaciones deben tener al menos un subproceso; el subproceso utilizado por su `CWinApp` objeto es este subproceso principal.

`CWinThread` Encapsula una parte de las capacidades de subprocesamiento del sistema operativo. Con el fin de usar varios subprocesos más fácil, MFC también proporciona a sincronización de las clases de objeto para proporcionar una interfaz de C++ para objetos de sincronización de Win32.

## <a name="application-and-thread-classes"></a>Clases de aplicación y subprocesos

[CWinApp](../mfc/reference/cwinapp-class.md)<br/>
Encapsula el código para inicializar, ejecutar y finalizar la aplicación. El objeto de aplicación derivará de esta clase.

[CWinThread](../mfc/reference/cwinthread-class.md)<br/>
La clase base para todos los subprocesos. Utilizar directamente o derivar una clase de `CWinThread` si el subproceso realiza funciones de interfaz de usuario. La clase `CWinApp` se deriva de la clase `CWinThread`.

## <a name="synchronization-object-classes"></a>Clases de objeto de sincronización

[CSyncObject](../mfc/reference/csyncobject-class.md)<br/>
Clase base de las clases de objeto de sincronización.

[CCriticalSection](../mfc/reference/ccriticalsection-class.md)<br/>
Una clase de sincronización que permite solo un subproceso en un único proceso para tener acceso a un objeto.

[CSemaphore](../mfc/reference/csemaphore-class.md)<br/>
Una clase de sincronización que permite entre uno y un número máximo especificado de accesos simultáneos a un objeto.

[CMutex](../mfc/reference/cmutex-class.md)<br/>
Una clase de sincronización que permite solo un subproceso dentro de cualquier número de procesos tengan acceso a un objeto.

[CEvent](../mfc/reference/cevent-class.md)<br/>
Una clase de sincronización que notifica a una aplicación cuando se ha producido un evento.

[CSingleLock](../mfc/reference/csinglelock-class.md)<br/>
Se utiliza en funciones miembro de clases seguras para subprocesos para bloquear en un objeto de sincronización.

[CMultiLock](../mfc/reference/cmultilock-class.md)<br/>
Se utiliza en funciones miembro de clases seguras para subprocesos para bloquear en uno o varios objetos de sincronización de una matriz de objetos de sincronización.

## <a name="related-classes"></a>Clases relacionadas

[CCommandLineInfo](../mfc/reference/ccommandlineinfo-class.md)<br/>
Analiza la línea de comandos con la que se inició el programa.

[CWaitCursor](../mfc/reference/cwaitcursor-class.md)<br/>
Coloca un cursor de espera en la pantalla. Se usa durante las operaciones largas.

[CDockState](../mfc/reference/cdockstate-class.md)<br/>
Controla el almacenamiento persistente de datos de estado de las barras de control de acoplamiento.

[CRecentFileList](../mfc/reference/crecentfilelist-class.md)<br/>
Mantiene la mayoría de la archivos usados recientemente (MRU).

## <a name="see-also"></a>Vea también

[Información general de clases](../mfc/class-library-overview.md)
