---
title: "Subprocesamiento m&#250;ltiple: Cu&#225;ndo utilizar las clases de sincronizaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "acceso controlado a los recursos [C++]"
  - "subprocesamiento múltiple [C++], clases de sincronización"
  - "recursos [C++], multithreading"
  - "sincronización [C++], multithreading"
  - "clases de sincronización de acceso [C++]"
  - "clases de sincronización [C++]"
  - "subprocesamiento [C++], sincronización"
  - "subprocesamiento [MFC], clases de sincronización"
ms.assetid: 4914f54e-68ac-438f-93c9-c013455a657e
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Subprocesamiento m&#250;ltiple: Cu&#225;ndo utilizar las clases de sincronizaci&#243;n
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las clases de multiproceso suministradas con MFC se dividen en dos categorías: objetos de sincronización \([CSyncObject](../../mfc/reference/csyncobject-class.md), [CSemaphore](../../mfc/reference/csemaphore-class.md), [CMutex](../../mfc/reference/cmutex-class.md), [CCriticalSection](../../mfc/reference/ccriticalsection-class.md) y [CEvent](../../mfc/reference/cevent-class.md)\) y objetos de sincronización de acceso \([CMultiLock](../../mfc/reference/cmultilock-class.md) y [CSingleLock](../../mfc/reference/csinglelock-class.md)\).  
  
 Las clases de sincronización se utilizan cuando es necesario controlar el acceso a un recurso para garantizar su integridad.  Las clases de sincronización de acceso se utilizan para obtener acceso a estos recursos controlados.  Este tema describe cuándo utilizar cada clase.  
  
 Para determinar qué clase de sincronización se debe utilizar, considere las siguientes preguntas:  
  
1.  ¿Debe esperar la aplicación a que ocurra algo para poder tener acceso al recurso \(por ejemplo, recibir datos de un puerto de comunicaciones antes de escribirlos en un archivo\)?  
  
     En caso afirmativo, utilice `CEvent`.  
  
2.  ¿Pueden obtener acceso al recurso varios subprocesos de la misma aplicación a la vez \(por ejemplo, la aplicación utiliza hasta cinco ventanas con vistas del mismo documento\)?  
  
     En caso afirmativo, utilice `CSemaphore`.  
  
3.  ¿Pueden utilizar varias aplicaciones este recurso \(por ejemplo, el recurso está en una DLL\)?  
  
     En caso afirmativo, utilice `CMutex`.  
  
     De lo contrario, utilice `CCriticalSection`.  
  
 **CSyncObject** no se utiliza nunca directamente.  Actúa como clase base para las otras cuatro clases de sincronización.  
  
## Ejemplo 1: utilizar tres clases de sincronización  
 Como ejemplo, considere una aplicación que mantiene una lista vinculada de cuentas.  Esta aplicación permite examinar hasta tres cuentas en ventanas independientes, pero sólo se puede actualizar una en un momento dado.  Cuando se actualiza una cuenta, los datos actualizados se envían a un archivo recopilatorio de datos.  
  
 Esta aplicación de ejemplo utiliza los tres tipos de clases de sincronización.  Como se pueden examinar hasta tres cuentas a la vez, se utiliza un `CSemaphore` para limitar el acceso a tres objetos de tipo vista.  Cuando se produce un intento de ver una cuarta cuenta, la aplicación espera a que se cierre una de las tres primeras ventanas o bien genera un error.  En el momento de actualizar una cuenta, la aplicación utiliza `CCriticalSection`para garantizar que sólo se actualiza una cada vez.  Si la actualización termina correctamente, la aplicación señaliza el evento `CEvent`, lo cual permite liberar un subproceso que se encontraba en espera de la señalización del evento.  Este subproceso envía los nuevos datos al archivo de almacenamiento de datos.  
  
## Ejemplo 2: utilizar las clases de sincronización de acceso  
 Elegir la clase de sincronización de acceso es incluso más sencillo.  Si la aplicación sólo va a tener acceso a un único recurso controlado, utilice `CSingleLock`.  Si necesita acceso a uno cualquiera de una serie de recursos controlados, utilice `CMultiLock`.  En el ejemplo 1, se habría utilizado `CSingleLock`, ya que en cada caso sólo se necesita un recurso en un momento dado.  
  
 Para obtener información sobre cómo utilizar las clases de sincronización, vea [Multithreading: Uso de las clases de sincronización](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  Para obtener información acerca de la sincronización, vea [Sincronización](http://msdn.microsoft.com/library/windows/desktop/ms686353) en [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)].  Para obtener información sobre la compatibilidad con el multithreading en MFC, vea [Multithreading con C\+\+ y MFC](../../parallel/multithreading-with-cpp-and-mfc.md).  
  
## Vea también  
 [Subprocesamiento múltiple con C\+\+ y MFC](../../parallel/multithreading-with-cpp-and-mfc.md)