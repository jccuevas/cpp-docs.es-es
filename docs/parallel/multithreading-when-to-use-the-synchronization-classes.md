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
ms.openlocfilehash: cb68487e036093ce4718c39c18c9d1e75afe0f7c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512000"
---
# <a name="multithreading-when-to-use-the-mfc-synchronization-classes"></a>Multithreading: Cuándo usar las clases de sincronización de MFC

Las clases multiproceso proporcionadas con MFC se dividen en dos categorías: objetos de sincronización ([CSyncObject](../mfc/reference/csyncobject-class.md), [CSemaphore](../mfc/reference/csemaphore-class.md), [CMutex](../mfc/reference/cmutex-class.md), [CCriticalSection](../mfc/reference/ccriticalsection-class.md)y [CEvent](../mfc/reference/cevent-class.md)) y objetos de acceso de sincronización ([ CMultiLock](../mfc/reference/cmultilock-class.md) y [CSingleLock](../mfc/reference/csinglelock-class.md)).

Las clases de sincronización se usan cuando se debe controlar el acceso a un recurso para garantizar la integridad del recurso. Las clases de acceso de sincronización se utilizan para obtener acceso a estos recursos controlados. En este tema se describe cuándo usar cada clase.

Para determinar qué clase de sincronización debe usar, consulte la siguiente serie de preguntas:

1. ¿La aplicación tiene que esperar a que suceda algo antes de que pueda tener acceso al recurso (por ejemplo, los datos se deben recibir de un puerto de comunicaciones antes de que se puedan escribir en un archivo)?

   En caso afirmativo `CEvent`, use.

2. ¿Puede tener más de un subproceso de la misma aplicación tener acceso a este recurso al mismo tiempo (por ejemplo, si la aplicación permite hasta cinco ventanas con vistas en el mismo documento)?

   En caso afirmativo `CSemaphore`, use.

3. ¿Puede más de una aplicación usar este recurso (por ejemplo, si el recurso está en un archivo DLL)?

   En caso afirmativo `CMutex`, use.

   Si no es así `CCriticalSection`, use.

`CSyncObject`nunca se usa directamente. Es la clase base para las otras cuatro clases de sincronización.

## <a name="example-1-using-three-synchronization-classes"></a>Ejemplo 1: Usar tres clases de sincronización

Como ejemplo, considere una aplicación que mantiene una lista vinculada de cuentas. Esta aplicación permite examinar hasta tres cuentas en ventanas independientes, pero sólo se puede actualizar una en un momento dado. Cuando se actualiza una cuenta, los datos actualizados se envían a un archivo recopilatorio de datos.

Esta aplicación de ejemplo utiliza los tres tipos de clases de sincronización. Dado que permite examinar hasta tres cuentas al mismo tiempo, utiliza `CSemaphore` para limitar el acceso a tres objetos de vista. Cuando se produce un intento de ver una cuarta cuenta, la aplicación espera a que se cierre una de las tres primeras ventanas o bien genera un error. Cuando se actualiza una cuenta, la aplicación usa `CCriticalSection` para asegurarse de que solo se actualiza una cuenta a la vez. Una vez que la actualización se realiza correctamente `CEvent`, indica que libera un subproceso en espera de que se señale el evento. Este subproceso envía los nuevos datos al archivo de almacenamiento de datos.

## <a name="example-2-using-synchronization-access-classes"></a>Ejemplo 2: Usar las clases de acceso de sincronización

La elección de la clase de acceso de sincronización que se va a usar es incluso más sencilla. Si su aplicación solo tiene acceso a un único recurso controlado, use `CSingleLock`. Si necesita tener acceso a una serie de recursos controlados, use `CMultiLock`. En el ejemplo 1 `CSingleLock` , se habría usado, porque en cada caso solo se necesita un recurso en un momento determinado.

Para obtener información sobre cómo se usan las clases de sincronización [, vea multithreading: Cómo usar las clases](multithreading-how-to-use-the-synchronization-classes.md)de sincronización. Para obtener información acerca de la sincronización, consulte [Synchronization](/windows/win32/Sync/synchronization) in the Windows SDK. Para obtener información sobre la compatibilidad con multithreading en MFC, vea multithreading [ C++ con y MFC](multithreading-with-cpp-and-mfc.md).

## <a name="see-also"></a>Vea también

[Multithreading con C++ y MFC](multithreading-with-cpp-and-mfc.md)
