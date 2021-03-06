---
title: 'Multithreading: Crear subprocesos de la interfaz de usuario de MFC'
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
ms.openlocfilehash: 1cd28a848f9be223f43412c3e0f3961cef9db6c7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512087"
---
# <a name="multithreading-creating-mfc-user-interface-threads"></a>Multithreading: Crear subprocesos de la interfaz de usuario de MFC

Los subprocesos de interfaz de usuario se utilizan normalmente para controlar los datos proporcionados por el usuario y para responder a los eventos de usuario independientemente de los subprocesos que ejecutan otras partes de la aplicación. El subproceso principal de la aplicación (suministrado en la clase derivada de `CWinApp`) ya está creado y se inicia automáticamente. Este tema describe los pasos necesarios para crear subprocesos de interfaz de usuario adicionales.

Lo primero que debe hacer cuando se crea un subproceso de interfaz de usuario es derivar una clase de [CWinThread](../mfc/reference/cwinthread-class.md). Debe declarar e implementar esta clase mediante las macros [DECLARE_DYNCREATE](../mfc/reference/run-time-object-model-services.md#declare_dyncreate) y [IMPLEMENT_DYNCREATE](../mfc/reference/run-time-object-model-services.md#implement_dyncreate) . Esta clase debe reemplazar algunas funciones y puede reemplazar otras. Estas funciones, y su cometido, se presentan en la siguiente tabla.

### <a name="functions-to-override-when-creating-a-user-interface-thread"></a>Funciones que se deben reemplazar cuando se crea un subproceso de interfaz de usuario

|Función|Propósito|
|--------------|-------------|
|[ExitInstance](../mfc/reference/cwinthread-class.md#exitinstance)|Realizar tareas de limpieza cuando el subproceso termina. Normalmente, se reemplaza.|
|[InitInstance](../mfc/reference/cwinthread-class.md#initinstance)|Llevar a cabo la inicialización de la instancia del subproceso. Debe reemplazarse.|
|[OnIdle](../mfc/reference/cwinthread-class.md#onidle)|Realizar el procesamiento de los tiempos de inactividad específicos del subproceso. No se suele reemplazar.|
|[PreTranslateMessage](../mfc/reference/cwinthread-class.md#pretranslatemessage)|Filtre los mensajes antes de enviarlos a `TranslateMessage` y. `DispatchMessage` No se suele reemplazar.|
|[ProcessWndProcException](../mfc/reference/cwinthread-class.md#processwndprocexception)|Interceptar las excepciones no controladas producidas por el mensaje del subproceso y activar los controladores. No se suele reemplazar.|
|[Run](../mfc/reference/cwinthread-class.md#run)|Función controladora para el subproceso. Contiene la fuente de mensajes. Casi nunca se reemplaza.|

MFC proporciona dos versiones de `AfxBeginThread` por medio de sobrecarga de parámetros: una que solo puede crear subprocesos de trabajo y otra que puede crear subprocesos de interfaz de usuario o subprocesos de trabajo. Para iniciar el subproceso de la interfaz de usuario, llame a la segunda sobrecarga de [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread)y proporcione la siguiente información:

- [RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class) de la clase de la que se `CWinThread`deriva.

- (Opcional) El nivel de prioridad deseado. El valor predeterminado es la prioridad normal. Para obtener más información sobre los niveles de prioridad disponibles, vea [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) en el Windows SDK.

- (Opcional) El tamaño de pila deseado para el subproceso. El valor predeterminado para el tamaño de pila es el mismo que el del subproceso creador.

- Opta CREATE_SUSPENDED si desea que el subproceso se cree en un estado suspendido. El valor predeterminado es 0, es decir, iniciar el subproceso normalmente.

- (Opcional) Los atributos de seguridad deseados. El valor predeterminado es el mismo acceso que el de su subproceso primario. Para obtener más información acerca del formato de esta información de seguridad, vea [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) en el Windows SDK.

`AfxBeginThread` realiza automáticamente la mayoría del trabajo. Crea un nuevo objeto de la clase, lo inicializa con la información proporcionada y llama a [CWinThread:: CreateThread](../mfc/reference/cwinthread-class.md#createthread) para empezar a ejecutar el subproceso. Se realizan comprobaciones en todo el procedimiento para asegurar que todos los objetos queden desasignados correctamente en caso de error en algún momento del proceso de creación.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

- [Multithreading: terminar subprocesos](multithreading-terminating-threads.md)

- [Multithreading: crear subprocesos de trabajo](multithreading-creating-worker-threads.md)

- [Procesos y subprocesos](/windows/win32/ProcThread/processes-and-threads)

## <a name="see-also"></a>Vea también

[Multithreading con C++ y MFC](multithreading-with-cpp-and-mfc.md)
