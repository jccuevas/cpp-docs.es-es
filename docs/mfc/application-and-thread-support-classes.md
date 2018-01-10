---
title: Clases de compatibilidad de aplicaciones y subprocesos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.support
dev_langs: C++
helpviewer_keywords:
- application objects [MFC], thread support classes
- lock classes [MFC]
- thread support classes [MFC]
- threading [MFC]
- synchronization classes [MFC], multithreading
- application support classes [MFC]
ms.assetid: 3c1d14fd-c35c-48f1-86ce-1e0f9a32c36d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e443c2393d9d3a8a0f61df6adddb2c83e7672723
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="application-and-thread-support-classes"></a>Clases de aplicación y de compatibilidad con subprocesos
Cada aplicación tiene uno y solo un objeto de aplicación; Este objeto coordina otros objetos en el programa en ejecución y se deriva de `CWinApp`.  
  
 La biblioteca (Microsoft Foundation Classes) es compatible con varios subprocesos de ejecución dentro de una aplicación. Todas las aplicaciones que deben tener al menos un subproceso; el subproceso utilizado por su `CWinApp` objeto es el subproceso principal.  
  
 `CWinThread`Encapsula una parte de las capacidades de subprocesos del sistema operativo. Para hacer que sea más fácil el uso de varios subprocesos, MFC proporciona también sincronización de las clases de objeto para proporcionar una interfaz de C++ para objetos de sincronización de Win32.  
  
## <a name="application-and-thread-classes"></a>Clases de aplicación y subprocesos  
 [CWinApp](../mfc/reference/cwinapp-class.md)  
 Encapsula el código para inicializar, ejecutar y finalizar la aplicación. El objeto application derivará de esta clase.  
  
 [CWinThread](../mfc/reference/cwinthread-class.md)  
 La clase base para todos los subprocesos. Usar directamente o derivar una clase de `CWinThread` si su subproceso realiza funciones de la interfaz de usuario. La clase `CWinApp` se deriva de la clase `CWinThread`.  
  
## <a name="synchronization-object-classes"></a>Clases de objeto de sincronización  
 [CSyncObject](../mfc/reference/csyncobject-class.md)  
 Clase base de las clases de objeto de sincronización.  
  
 [CCriticalSection](../mfc/reference/ccriticalsection-class.md)  
 Una clase de sincronización que permite que un solo subproceso dentro de un proceso único para tener acceso a un objeto.  
  
 [CSemaphore](../mfc/reference/csemaphore-class.md)  
 Una clase de sincronización que permite que haya entre uno y un número máximo especificado de accesos simultáneos en el objeto.  
  
 [CMutex](../mfc/reference/cmutex-class.md)  
 Una clase de sincronización que permite que un solo subproceso dentro de cualquier número de procesos tengan acceso a un objeto.  
  
 [CEvent](../mfc/reference/cevent-class.md)  
 Una clase de sincronización que notifica a una aplicación cuando se ha producido un evento.  
  
 [CSingleLock](../mfc/reference/csinglelock-class.md)  
 Se utilizan en las funciones miembro de clases seguras para subprocesos para bloquear en un objeto de sincronización.  
  
 [CMultiLock](../mfc/reference/cmultilock-class.md)  
 Se utilizan en las funciones miembro de clases seguras para subprocesos para bloquear en uno o varios objetos de sincronización de una matriz de objetos de sincronización.  
  
## <a name="related-classes"></a>Clases relacionadas  
 [CCommandLineInfo](../mfc/reference/ccommandlineinfo-class.md)  
 Analiza la línea de comandos con la que se inició el programa.  
  
 [CWaitCursor](../mfc/reference/cwaitcursor-class.md)  
 Coloca un cursor de espera en la pantalla. Se utiliza durante las operaciones largas.  
  
 [CDockState](../mfc/reference/cdockstate-class.md)  
 Controla el almacenamiento persistente de datos de estado para las barras de control de acoplamiento.  
  
 [CRecentFileList](../mfc/reference/crecentfilelist-class.md)  
 Mantiene la mayoría de la archivos usados recientemente (MRU).  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../mfc/class-library-overview.md)

