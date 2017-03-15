---
title: "Clases de aplicaci&#243;n y de compatibilidad con subprocesos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.support"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "objetos de aplicación [C++], subproceso que admite clases"
  - "clases de aplicación y de compatibilidad [C++]"
  - "bloquear clases"
  - "clases de sincronización, multithreading"
  - "subproceso que admite clases [C++]"
  - "subprocesamiento [MFC]"
ms.assetid: 3c1d14fd-c35c-48f1-86ce-1e0f9a32c36d
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Clases de aplicaci&#243;n y de compatibilidad con subprocesos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cada aplicación tiene solo un objeto application; este objeto coordina otros objetos del programa en ejecución y se deriva de `CWinApp`.  
  
 La biblioteca de \(MFC\) de la clase de la base de Microsoft admite varios subprocesos de ejecución dentro de una aplicación.  Todas las aplicaciones deben tener al menos un subproceso; el subproceso utilizado por el objeto de `CWinApp` es este subproceso primario.  
  
 `CWinThread` encapsula una parte de las capacidades de subprocesamiento del sistema operativo.  Para crear mediante varios subprocesos más fácil, MFC también proporciona clases de objeto de sincronización para proporcionar la interfaz de c\+\+. para los objetos de sincronización de Win32.  
  
## Clases de aplicación y subprocesos  
 [CWinApp](../mfc/reference/cwinapp-class.md)  
 Encapsula el código para inicializar, ejecutar, y para finalizar la aplicación.  Se derivará el objeto application de esta clase.  
  
 [CWinThread](../mfc/reference/cwinthread-class.md)  
 La clase base para todos los subprocesos.  Utilice directamente, o derivando una clase de `CWinThread` si el subproceso realiza funciones de la interfaz de usuario.  `CWinApp` se deriva de `CWinThread`.  
  
## Clases de objeto de sincronización  
 [CSyncObject](../mfc/reference/csyncobject-class.md)  
 Clase base de las clases de objeto de sincronización.  
  
 [CCriticalSection](../mfc/reference/ccriticalsection-class.md)  
 Una clase de sincronización que permite que sólo un subproceso en un solo proceso tiene acceso a un objeto.  
  
 [CSemaphore](../mfc/reference/csemaphore-class.md)  
 Una clase de sincronización que permite entre uno y un número máximo especificado de accesos simultáneos a un objeto.  
  
 [CMutex](../mfc/reference/cmutex-class.md)  
 Una clase de sincronización que permite que sólo un subproceso dentro de cualquier número de procesos tengan acceso a un objeto.  
  
 [CEvent](../mfc/reference/cevent-class.md)  
 Una clase de sincronización que notifica a una aplicación cuando se ha producido un evento.  
  
 [CSingleLock](../mfc/reference/csinglelock-class.md)  
 Se utiliza en funciones miembro de clases seguras para subprocesos para bloquear en un objeto de sincronización.  
  
 [CMultiLock](../mfc/reference/cmultilock-class.md)  
 Se utiliza en funciones miembro de clases seguras para subprocesos para bloquear en uno o más objetos de sincronización de una matriz de objetos de sincronización.  
  
## Clases relacionadas  
 [CCommandLineInfo](../mfc/reference/ccommandlineinfo-class.md)  
 Analiza la línea de comandos con la que el programa se inició.  
  
 [CWaitCursor](../mfc/reference/cwaitcursor-class.md)  
 Coloca una espera el cursor en la pantalla.  Utilizado durante operaciones largas.  
  
 [CDockState](../mfc/reference/cdockstate-class.md)  
 Controla el almacenamiento permanente de los datos de estado de vinculación de las barras de control.  
  
 [CRecentFileList](../mfc/reference/crecentfilelist-class.md)  
 Mantiene la lista de archivos usados recientemente utilizada de \(MRU\).  
  
## Vea también  
 [Información general de clases](../mfc/class-library-overview.md)