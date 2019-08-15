---
title: 'Multithreading: Cómo usar las clases de sincronización de MFC'
ms.date: 08/27/2018
helpviewer_keywords:
- MFC [C++], multithreading
- threading [MFC], synchronization classes
- resources [C++], multithreading
- thread-safe classes [C++]
- synchronization classes [C++]
- synchronization [C++], multithreading
- threading [MFC], thread-safe class design
- threading [C++], synchronization
- multithreading [C++], synchronization classes
- threading [C++], thread-safe class design
ms.assetid: f266d4c6-0454-4bda-9758-26157ef74cc5
ms.openlocfilehash: 26a059e378edb92f5ff7f4e788ded90678e0c129
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511875"
---
# <a name="multithreading-how-to-use-the-mfc-synchronization-classes"></a>Multithreading: Cómo usar las clases de sincronización de MFC

Sincronizar el acceso a los recursos entre subprocesos es un problema habitual cuando se escriben aplicaciones multiproceso. Si dos o más subprocesos tienen acceso a los mismos datos simultáneamente, se pueden producir resultados impredecibles y no deseados. Por ejemplo, un subproceso podría estar actualizando el contenido de una estructura mientras que otro está leyendo el contenido de la misma estructura. No se puede saber qué datos recibirá el proceso de lectura: los datos antiguos, los datos recién escritos o, posiblemente, una mezcla de ambos. MFC proporciona una serie de clases de sincronización y de sincronización de acceso para contribuir a resolver este problema. Este tema describe las clases disponibles y su uso con el fin de crear clases seguras para subprocesos en una aplicación multiproceso típica.

Una aplicación multiproceso múltiple típica dispone de una clase que representa un recurso que se va a compartir entre subprocesos. Una clase bien diseñada completamente segura para la ejecución de subprocesos no requiere que el programador llame a ninguna función de sincronización. Todo se controla internamente en la clase; por tanto, el programador se puede concentrar en la mejor forma de usar la clase, no en si ésta puede resultar dañada por algún error. Una técnica eficaz para crear una clase segura para la ejecución de subprocesos consiste en integrar la clase de sincronización en la clase del recurso. La integración de clases de sincronización en la clase compartida es un proceso sencillo.

Como ejemplo, considere una aplicación que mantiene una lista vinculada de cuentas. Esta aplicación permite examinar hasta tres cuentas en ventanas independientes, pero sólo se puede actualizar una en un momento dado. Cuando se actualiza una cuenta, los datos actualizados se envían a un archivo recopilatorio de datos.

Esta aplicación de ejemplo utiliza los tres tipos de clases de sincronización. Dado que permite examinar hasta tres cuentas al mismo tiempo, utiliza el [CSemaphore](../mfc/reference/csemaphore-class.md) para limitar el acceso a tres objetos de vista. Cuando se produce un intento de ver una cuarta cuenta, la aplicación espera a que se cierre una de las tres primeras ventanas o bien genera un error. Cuando se actualiza una cuenta, la aplicación usa [CCriticalSection](../mfc/reference/ccriticalsection-class.md) para asegurarse de que solo se actualiza una cuenta a la vez. Una vez que la actualización se realiza correctamente, señala [CEvent](../mfc/reference/cevent-class.md), que libera un subproceso en espera de que se señale el evento. Este subproceso envía los nuevos datos al archivo de almacenamiento de datos.

##  <a name="_mfc_designing_a_thread.2d.safe_class"></a>Diseñar una clase segura para subprocesos

Para hacer que una clase sea completamente segura para la ejecución de subprocesos, primero agregue la clase de sincronización apropiada a las clases compartidas como un miembro de datos. En el ejemplo anterior de administración de cuentas, `CSemaphore` se agregaría un miembro de datos a la clase de `CCriticalSection` vista, un miembro de datos se agregaría a la clase de lista `CEvent` vinculada y se agregaría un miembro de datos a la clase de almacenamiento de datos.

A continuación, agregue llamadas de sincronización a todas las funciones miembro que modifican los datos de la clase o que tienen acceso a un recurso controlado. En cada función, debe crear un objeto [CSingleLock](../mfc/reference/csinglelock-class.md) o [CMultiLock](../mfc/reference/cmultilock-class.md) y llamar a la función de `Lock` ese objeto. Cuando el objeto de bloqueo queda fuera de ámbito y se destruye, el destructor del objeto llama automáticamente a `Unlock` y libera el recurso. No obstante, puede realizar una llamada a `Unlock` directamente si lo desea.

El diseño de una clase segura para subprocesos realizado de esta forma permite utilizarla en aplicaciones multiproceso con la misma facilidad que una clase no diseñada para subprocesos, pero con un nivel muy alto de seguridad. La encapsulación del objeto de sincronización y del objeto de sincronización de acceso en la clase del recurso proporciona todas las ventajas de la programación segura para subprocesos sin los inconvenientes de mantener el código encargado de la sincronización.

El siguiente ejemplo de código ilustra este método mediante el uso de un miembro de datos, `m_CritSection` (de tipo `CCriticalSection`), declarado en la clase del recurso compartido, y un objeto `CSingleLock`. La sincronización del recurso compartido (derivado de `CWinThread`) se lleva a cabo mediante la creación de un objeto `CSingleLock` que utiliza la dirección del objeto `m_CritSection`. Se realiza un intento de bloquear el recurso y, una vez conseguido, se realiza la tarea sobre el objeto compartido. Tras finalizar la tarea, el recurso se desbloquea mediante una llamada a `Unlock`.

```
CSingleLock singleLock(&m_CritSection);
singleLock.Lock();
// resource locked
//.usage of shared resource...

singleLock.Unlock();
```

> [!NOTE]
> `CCriticalSection`, a diferencia de otras clases de sincronización de MFC, no dispone de la opción de solicitud de bloqueo temporizado. El período de espera para que un subproceso se libere es infinito.

El inconveniente de este enfoque es que la clase será ligeramente más lenta que la misma clase sin los objetos de sincronización agregados. Además, si existe la posibilidad de que varios subprocesos puedan eliminar el objeto, el enfoque de integración no siempre funcionará. En esta situación, es mejor mantener objetos de sincronización independientes.

Para obtener información sobre cómo determinar la clase de sincronización que se va a [usar en situaciones diferentes, vea multithreading: Cuándo usar las clases](multithreading-when-to-use-the-synchronization-classes.md)de sincronización. Para obtener más información acerca de la sincronización, consulte [Synchronization](/windows/win32/Sync/synchronization) in the Windows SDK. Para obtener más información acerca de la compatibilidad con multithreading en MFC, vea multithreading [ C++ con y MFC](multithreading-with-cpp-and-mfc.md).

## <a name="see-also"></a>Vea también

[Multithreading con C++ y MFC](multithreading-with-cpp-and-mfc.md)
