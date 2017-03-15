---
title: "Subprocesamiento m&#250;ltiple: Uso de las clases de sincronizaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC [C++], multithreading"
  - "subprocesamiento múltiple [C++], clases de sincronización"
  - "recursos [C++], multithreading"
  - "sincronización [C++], multithreading"
  - "clases de sincronización [C++]"
  - "subprocesamiento [C++], sincronización"
  - "subprocesamiento [C++], diseño de clases seguras para subprocesos"
  - "subprocesamiento [MFC], clases de sincronización"
  - "subprocesamiento [MFC], diseño de clases seguras para subprocesos"
  - "clases seguras para subprocesos [C++]"
ms.assetid: f266d4c6-0454-4bda-9758-26157ef74cc5
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Subprocesamiento m&#250;ltiple: Uso de las clases de sincronizaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Sincronizar el acceso a los recursos entre subprocesos es un problema habitual cuando se escriben aplicaciones multiproceso.  Si dos o más subprocesos tienen acceso a los mismos datos simultáneamente, se pueden producir resultados impredecibles y no deseados.  Por ejemplo, un subproceso podría estar actualizando el contenido de una estructura mientras que otro está leyendo el contenido de la misma estructura.  No se puede saber qué datos recibirá el proceso de lectura: los datos antiguos, los datos recién escritos o, posiblemente, una mezcla de ambos.  MFC proporciona una serie de clases de sincronización y de sincronización de acceso para contribuir a resolver este problema.  Este tema describe las clases disponibles y su uso con el fin de crear clases seguras para subprocesos en una aplicación multiproceso típica.  
  
 Una aplicación multiproceso múltiple típica dispone de una clase que representa un recurso que se va a compartir entre subprocesos.  Una clase bien diseñada completamente segura para la ejecución de subprocesos no requiere que el programador llame a ninguna función de sincronización.  Todo se controla internamente en la clase; por tanto, el programador se puede concentrar en la mejor forma de usar la clase, no en si ésta puede resultar dañada por algún error.  Una técnica eficaz para crear una clase segura para la ejecución de subprocesos consiste en integrar la clase de sincronización en la clase del recurso.  La integración de clases de sincronización en la clase compartida es un proceso sencillo.  
  
 Como ejemplo, considere una aplicación que mantiene una lista vinculada de cuentas.  Esta aplicación permite examinar hasta tres cuentas en ventanas independientes, pero sólo se puede actualizar una en un momento dado.  Cuando se actualiza una cuenta, los datos actualizados se envían a un archivo recopilatorio de datos.  
  
 Esta aplicación de ejemplo utiliza los tres tipos de clases de sincronización.  Como se pueden examinar hasta tres cuentas a la vez, se utiliza un objeto de sincronización [CSemaphore](../mfc/reference/csemaphore-class.md) para limitar el acceso a tres objetos de tipo vista.  Cuando se produce un intento de ver una cuarta cuenta, la aplicación espera a que se cierre una de las tres primeras ventanas o bien genera un error.  En el momento de actualizar una cuenta, la aplicación utiliza el objeto de sincronización [CCriticalSection](../mfc/reference/ccriticalsection-class.md) para garantizar que sólo se actualiza una cuenta cada vez.  Si la actualización termina correctamente, la aplicación señaliza el evento [CEvent](../mfc/reference/cevent-class.md), lo cual permite liberar un subproceso que se encontraba en espera de la señalización del evento.  Este subproceso envía los nuevos datos al archivo de almacenamiento de datos.  
  
##  <a name="_mfc_designing_a_thread.2d.safe_class"></a> Diseñar una clase segura para subprocesos  
 Para hacer que una clase sea completamente segura para la ejecución de subprocesos, primero agregue la clase de sincronización apropiada a las clases compartidas como un miembro de datos.  En el ejemplo anterior de administración de cuentas, se agregaría un miembro de datos **CSemaphore** a la clase de tipo vista, un miembro de datos `CCriticalSection` a la clase de lista vinculada y un miembro de datos `CEvent` a la clase de almacenamiento de datos.  
  
 A continuación, agregue llamadas de sincronización a todas las funciones miembro que modifican los datos de la clase o que tienen acceso a un recurso controlado.  En cada función, se debe crear un objeto [CSingleLock](../mfc/reference/csinglelock-class.md) o [CMultiLock](../mfc/reference/cmultilock-class.md) y llamar a la función `Lock` de ese objeto.  Cuando el objeto de bloqueo queda fuera de ámbito y se destruye, el destructor del objeto llama automáticamente a `Unlock` y libera el recurso.  No obstante, puede realizar una llamada a `Unlock` directamente si lo desea.  
  
 El diseño de una clase segura para subprocesos realizado de esta forma permite utilizarla en aplicaciones multiproceso con la misma facilidad que una clase no diseñada para subprocesos, pero con un nivel muy alto de seguridad.  La encapsulación del objeto de sincronización y del objeto de sincronización de acceso en la clase del recurso proporciona todas las ventajas de la programación segura para subprocesos sin los inconvenientes de mantener el código encargado de la sincronización.  
  
 El siguiente ejemplo de código ilustra este método mediante el uso de un miembro de datos, `m_CritSection` \(de tipo `CCriticalSection`\), declarado en la clase del recurso compartido, y un objeto `CSingleLock`.  La sincronización del recurso compartido \(derivado de `CWinThread`\) se lleva a cabo mediante la creación de un objeto `CSingleLock` que utiliza la dirección del objeto `m_CritSection`.  Se realiza un intento de bloquear el recurso y, una vez conseguido, se realiza la tarea sobre el objeto compartido.  Tras finalizar la tarea, el recurso se desbloquea mediante una llamada a `Unlock`.  
  
```  
CSingleLock singleLock(&m_CritSection);  
singleLock.Lock();  
// resource locked  
//.usage of shared resource...  
  
singleLock.Unlock();  
```  
  
> [!NOTE]
>  `CCriticalSection`, a diferencia de otras clases de sincronización de MFC, no dispone de la opción de solicitud de bloqueo temporizado.  El período de espera para que un subproceso se libere es infinito.  
  
 El inconveniente de este enfoque es que la clase será ligeramente más lenta que la misma clase sin los objetos de sincronización agregados.  Además, si existe la posibilidad de que varios subprocesos puedan eliminar el objeto, el enfoque de integración no siempre funcionará.  En esta situación, es mejor mantener objetos de sincronización independientes.  
  
 Para obtener información acerca de la determinación de la clase de sincronización que se debe utilizar según la situación, vea [Multithreading: Cuándo utilizar las clases de sincronización](../parallel/multithreading-when-to-use-the-synchronization-classes.md).  Para obtener más información acerca de la sincronización, vea [Sincronización](http://msdn.microsoft.com/library/windows/desktop/ms686353) en [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)].  Para obtener más información sobre la compatibilidad con el multithreading en MFC, vea [Multithreading con C\+\+ y MFC](../parallel/multithreading-with-cpp-and-mfc.md).  
  
## Vea también  
 [Subprocesamiento múltiple con C\+\+ y MFC](../parallel/multithreading-with-cpp-and-mfc.md)