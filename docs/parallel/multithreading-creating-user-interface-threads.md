---
title: 'Multithreading: Crear subprocesos de interfaz de usuario MFC'
ms.date: 08/27/2018
f1_keywords:
- CREATE_SUSPENDED
- SECURITY_ATTRIBUTES
helpviewer_keywords:
- multithreading [C++], user interface threads
- threading [C++], creating threads
- threading [C++], user interface threads
- user interface threads [C++]
- threading [MFC], user interface threads
ms.assetid: 446925c1-db59-46ea-ae5b-d5ae5d5b91d8
ms.openlocfilehash: ac22fad95041b07e132d31a2d246e58c3b40d30c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57293321"
---
# <a name="multithreading-creating-mfc-user-interface-threads"></a>Multithreading: Crear subprocesos de interfaz de usuario MFC

Los subprocesos de interfaz de usuario se utilizan normalmente para controlar los datos proporcionados por el usuario y para responder a los eventos de usuario independientemente de los subprocesos que ejecutan otras partes de la aplicación. El subproceso principal de la aplicación (suministrado en la clase derivada de `CWinApp`) ya está creado y se inicia automáticamente. Este tema describe los pasos necesarios para crear subprocesos de interfaz de usuario adicionales.

Lo primero que debe hacer al crear un subproceso de interfaz de usuario es derivar una clase de [CWinThread](../mfc/reference/cwinthread-class.md). Se debe declarar e implementar esta clase, utilizando el [DECLARE_DYNCREATE](../mfc/reference/run-time-object-model-services.md#declare_dyncreate) y [IMPLEMENT_DYNCREATE](../mfc/reference/run-time-object-model-services.md#implement_dyncreate) macros. Esta clase debe reemplazar algunas funciones y puede reemplazar otras. Estas funciones, y su cometido, se presentan en la siguiente tabla.

### <a name="functions-to-override-when-creating-a-user-interface-thread"></a>Funciones que se deben reemplazar cuando se crea un subproceso de interfaz de usuario

|Función|Propósito|
|--------------|-------------|
|[ExitInstance](../mfc/reference/cwinthread-class.md#exitinstance)|Realizar tareas de limpieza cuando el subproceso termina. Normalmente, se reemplaza.|
|[InitInstance](../mfc/reference/cwinthread-class.md#initinstance)|Llevar a cabo la inicialización de la instancia del subproceso. Debe reemplazarse.|
|[OnIdle](../mfc/reference/cwinthread-class.md#onidle)|Realizar el procesamiento de los tiempos de inactividad específicos del subproceso. No se suele reemplazar.|
|[PreTranslateMessage](../mfc/reference/cwinthread-class.md#pretranslatemessage)|Filtrar los mensajes antes de enviarlos a `TranslateMessage` y `DispatchMessage`. No se suele reemplazar.|
|[ProcessWndProcException](../mfc/reference/cwinthread-class.md#processwndprocexception)|Interceptar las excepciones no controladas producidas por el mensaje del subproceso y activar los controladores. No se suele reemplazar.|
|[Run](../mfc/reference/cwinthread-class.md#run)|Función controladora para el subproceso. Contiene la fuente de mensajes. Casi nunca se reemplaza.|

MFC proporciona dos versiones de `AfxBeginThread` por medio de sobrecarga de parámetros: una que solo puede crear subprocesos de trabajo y otra que puede crear subprocesos de interfaz de usuario o subprocesos de trabajo. Para iniciar el subproceso de interfaz de usuario, llame a la segunda sobrecarga de [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), proporcione la información siguiente:

- El [RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class) de la clase que deriva de `CWinThread`.

- (Opcional) El nivel de prioridad deseado. El valor predeterminado es la prioridad normal. Para obtener más información acerca de los niveles de prioridad disponibles, vea [SetThreadPriority](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) en el SDK de Windows.

- (Opcional) El tamaño de pila deseado para el subproceso. El valor predeterminado para el tamaño de pila es el mismo que el del subproceso creador.

- (Opcional) CREATE_SUSPENDED si desea que el subproceso que se creará en un estado suspendido. El valor predeterminado es 0, es decir, iniciar el subproceso normalmente.

- (Opcional) Los atributos de seguridad deseados. El valor predeterminado es el mismo acceso que el de su subproceso primario. Para obtener más información sobre el formato de esta información de seguridad, consulte [SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) en el SDK de Windows.

`AfxBeginThread` realiza automáticamente la mayoría del trabajo. Crea un nuevo objeto de la clase, lo inicializa con la información suministrada y llama a [CWinThread:: CreateThread](../mfc/reference/cwinthread-class.md#createthread) para empezar a ejecutar el subproceso. Se realizan comprobaciones en todo el procedimiento para asegurar que todos los objetos queden desasignados correctamente en caso de error en algún momento del proceso de creación.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Multithreading: Terminar subprocesos](multithreading-terminating-threads.md)

- [Multithreading: Crear subprocesos de trabajo](multithreading-creating-worker-threads.md)

- [Los procesos y subprocesos](/windows/desktop/ProcThread/processes-and-threads)

## <a name="see-also"></a>Vea también

[Multithreading con C++ y MFC](multithreading-with-cpp-and-mfc.md)
