---
title: 'Multithreading: Cuándo usar las clases de sincronización de MFC'
ms.date: 08/27/2018
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
ms.openlocfilehash: 72cf5310704c1ae959cc012146a03dd32cff4068
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407658"
---
# <a name="multithreading-when-to-use-the-mfc-synchronization-classes"></a>Multithreading: Cuándo usar las clases de sincronización de MFC

Las clases de multiproceso suministradas con MFC se dividen en dos categorías: objetos de sincronización ([CSyncObject](../mfc/reference/csyncobject-class.md), [CSemaphore](../mfc/reference/csemaphore-class.md), [CMutex](../mfc/reference/cmutex-class.md), [ CCriticalSection](../mfc/reference/ccriticalsection-class.md), y [CEvent](../mfc/reference/cevent-class.md)) y obtener acceso a objetos de sincronización ([CMultiLock](../mfc/reference/cmultilock-class.md) y [CSingleLock](../mfc/reference/csinglelock-class.md)).

Clases de sincronización se usan cuando debe controlar el acceso a un recurso para garantizar la integridad del recurso. Clases de sincronización de acceso se utilizan para tener acceso a estos recursos controlados. Este tema describe cuándo usar cada clase.

Para determinar qué clase de sincronización se debe utilizar, hágase la siguiente serie de preguntas:

1. ¿La aplicación tiene que esperar algo que ocurra antes de pueda acceder al recurso (por ejemplo, datos se deben recibir desde un puerto de comunicaciones antes de se puede escribir en un archivo)?

   En caso afirmativo, utilice `CEvent`.

2. ¿Puede más de un subproceso dentro de la misma aplicación acceda a este recurso al mismo tiempo (por ejemplo, la aplicación permite hasta cinco ventanas con vistas en el mismo documento)?

   En caso afirmativo, utilice `CSemaphore`.

3. ¿Pueden usar de varias aplicaciones este recurso (por ejemplo, el recurso está en un archivo DLL)?

   En caso afirmativo, utilice `CMutex`.

   Si no, utilice `CCriticalSection`.

`CSyncObject` nunca se usa directamente. Es la clase base para las otras cuatro clases de sincronización.

## <a name="example-1-using-three-synchronization-classes"></a>Ejemplo 1: Uso de tres clases de sincronización

Como ejemplo, considere una aplicación que mantiene una lista vinculada de cuentas. Esta aplicación permite examinar hasta tres cuentas en ventanas independientes, pero sólo se puede actualizar una en un momento dado. Cuando se actualiza una cuenta, los datos actualizados se envían a un archivo recopilatorio de datos.

Esta aplicación de ejemplo utiliza los tres tipos de clases de sincronización. Porque permite hasta tres cuentas que se va a examinar al mismo tiempo, usa `CSemaphore` para limitar el acceso a tres objetos de vista. Cuando se produce un intento de ver una cuarta cuenta, la aplicación espera a que se cierre una de las tres primeras ventanas o bien genera un error. Cuando se actualiza una cuenta, la aplicación utiliza `CCriticalSection` para asegurarse de que se actualiza solo una cuenta a la vez. La actualización se realiza correctamente, la aplicación señaliza `CEvent`, lo que libera un subproceso en espera para que se señale el evento. Este subproceso envía los nuevos datos al archivo de almacenamiento de datos.

## <a name="example-2-using-synchronization-access-classes"></a>Ejemplo 2: Uso de clases de acceso de sincronización

Elegir qué clase de acceso de sincronización debe utilizar es incluso más sencillo. Si la aplicación es tener acceso a solo un único recurso controlado, utilice `CSingleLock`. Si necesita acceso a cualquiera de una serie de recursos controlados, utilice `CMultiLock`. En el ejemplo 1, `CSingleLock` habría utilizado, ya que en cada caso se necesita solo un recurso en un momento dado.

Para obtener información sobre cómo se utilizan las clases de sincronización, vea [Multithreading: Cómo usar las clases de sincronización](multithreading-how-to-use-the-synchronization-classes.md). Para obtener información acerca de la sincronización, vea [sincronización](/windows/desktop/Sync/synchronization) en el SDK de Windows. Para obtener información sobre la compatibilidad con multithreading en MFC, vea [Multithreading con C++ y MFC](multithreading-with-cpp-and-mfc.md).

## <a name="see-also"></a>Vea también

[Multithreading con C++ y MFC](multithreading-with-cpp-and-mfc.md)
