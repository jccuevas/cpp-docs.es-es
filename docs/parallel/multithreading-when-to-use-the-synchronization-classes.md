---
title: "Subprocesamiento múltiple: Cuándo utilizar las clases de sincronización | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- threading [MFC], synchronization classes
- resources [C++], multithreading
- synchronization classes [C++]
- synchronization [C++], multithreading
- controlled resource access [C++]
- synchronization access classes [C++]
- threading [C++], synchronization
- multithreading [C++], synchronization classes
ms.assetid: 4914f54e-68ac-438f-93c9-c013455a657e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 38437983552dfdf2cf6708ec5fd067e06387ea5c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="multithreading-when-to-use-the-synchronization-classes"></a>Subprocesamiento múltiple: Cuándo utilizar las clases de sincronización
Las clases de multiproceso suministradas con MFC se dividen en dos categorías: objetos de sincronización ([CSyncObject](../mfc/reference/csyncobject-class.md), [CSemaphore](../mfc/reference/csemaphore-class.md), [CMutex](../mfc/reference/cmutex-class.md), [ CCriticalSection](../mfc/reference/ccriticalsection-class.md), y [CEvent](../mfc/reference/cevent-class.md)) y obtener acceso a objetos de sincronización ([CMultiLock](../mfc/reference/cmultilock-class.md) y [CSingleLock](../mfc/reference/csinglelock-class.md)).  
  
 Clases de sincronización se utilizan cuando se debe controlar el acceso a un recurso para garantizar la integridad del recurso. Clases de sincronización de acceso se utilizan para obtener acceso a estos recursos controlados. Este tema describe cuándo utilizar cada clase.  
  
 Para determinar qué clase de sincronización que se debe usar, realiza la siguiente serie de preguntas:  
  
1.  ¿La aplicación tiene que esperar algo que se produzca antes de que puede tener acceso al recurso (por ejemplo, datos se deben recibir desde un puerto de comunicaciones antes de se puede escribir en un archivo)?  
  
     En caso afirmativo, use `CEvent`.  
  
2.  ¿Puede más de un subproceso dentro de la misma aplicación acceda a este recurso al mismo tiempo (por ejemplo, la aplicación permite hasta cinco ventanas con vistas en el mismo documento)?  
  
     En caso afirmativo, use `CSemaphore`.  
  
3.  ¿Puede usar más de una aplicación de este recurso (por ejemplo, el recurso está en un archivo DLL)?  
  
     En caso afirmativo, use `CMutex`.  
  
     Si no, utilice `CCriticalSection`.  
  
 **CSyncObject** nunca se utiliza directamente. Es la clase base para las otras cuatro clases de sincronización.  
  
## <a name="example-1-using-three-synchronization-classes"></a>Ejemplo 1: Utilizar tres clases de sincronización  
 Como ejemplo, considere una aplicación que mantiene una lista vinculada de cuentas. Esta aplicación permite examinar hasta tres cuentas en ventanas independientes, pero sólo se puede actualizar una en un momento dado. Cuando se actualiza una cuenta, los datos actualizados se envían a un archivo recopilatorio de datos.  
  
 Esta aplicación de ejemplo utiliza los tres tipos de clases de sincronización. Porque permite hasta tres cuentas examinar al mismo tiempo, utiliza `CSemaphore` para limitar el acceso a tres objetos de vista. Cuando se produce un intento de ver una cuarta cuenta, la aplicación espera a que se cierre una de las tres primeras ventanas o bien genera un error. Cuando se actualiza una cuenta, la aplicación utiliza `CCriticalSection` para asegurarse de que se actualiza una cuenta a la vez. La actualización se realiza correctamente, la aplicación señaliza `CEvent`, lo cual permite liberar un subproceso que espera del evento que se va a señalar. Este subproceso envía los nuevos datos al archivo de almacenamiento de datos.  
  
## <a name="example-2-using-synchronization-access-classes"></a>Ejemplo 2: Utilizar clases de sincronización de acceso  
 Elegir qué clase de acceso de sincronización debe usar es incluso más sencillo. Si la aplicación va a tener acceso a solo un único recurso controlado, utilice `CSingleLock`. Si necesita tener acceso a cualquiera de una serie de recursos controlados, utilice `CMultiLock`. En el ejemplo 1, `CSingleLock` habría usado, ya que en cada caso se necesita solo un recurso en un momento dado.  
  
 Para obtener información sobre cómo se utilizan las clases de sincronización, vea [subprocesamiento múltiple: cómo usar las clases de sincronización](../parallel/multithreading-how-to-use-the-synchronization-classes.md). Para obtener información acerca de la sincronización, vea [sincronización](http://msdn.microsoft.com/library/windows/desktop/ms686353) en el [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]. Para obtener información sobre la compatibilidad con multithreading en MFC, vea [Multithreading con C++ y MFC](../parallel/multithreading-with-cpp-and-mfc.md).  
  
## <a name="see-also"></a>Vea también  
 [Multithreading con C++ y MFC](../parallel/multithreading-with-cpp-and-mfc.md)