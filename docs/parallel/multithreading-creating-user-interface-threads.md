---
title: 'Multithreading: Crear subprocesos de interfaz de usuario | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CREATE_SUSPENDED
- SECURITY_ATTRIBUTES
dev_langs: C++
helpviewer_keywords:
- multithreading [C++], user interface threads
- threading [C++], creating threads
- threading [C++], user interface threads
- user interface threads [C++]
- threading [MFC], user interface threads
ms.assetid: 446925c1-db59-46ea-ae5b-d5ae5d5b91d8
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 105685e0db4689978ef1e6f8615bb5e5f8acdd43
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="multithreading-creating-user-interface-threads"></a>Subprocesamiento múltiple: Crear subprocesos de la interfaz de usuario
Los subprocesos de interfaz de usuario se utilizan normalmente para controlar los datos proporcionados por el usuario y para responder a los eventos de usuario independientemente de los subprocesos que ejecutan otras partes de la aplicación. El subproceso principal de la aplicación (suministrado en la clase derivada de `CWinApp`) ya está creado y se inicia automáticamente. Este tema describe los pasos necesarios para crear subprocesos de interfaz de usuario adicionales.  
  
 Lo primero que debe hacer al crear un subproceso de interfaz de usuario es derivar una clase de [CWinThread](../mfc/reference/cwinthread-class.md). Se debe declarar e implementar esta clase, usando la [DECLARE_DYNCREATE](../mfc/reference/run-time-object-model-services.md#declare_dyncreate) y [IMPLEMENT_DYNCREATE](../mfc/reference/run-time-object-model-services.md#implement_dyncreate) macros. Esta clase debe reemplazar algunas funciones y puede reemplazar otras. Estas funciones, y su cometido, se presentan en la siguiente tabla.  
  
### <a name="functions-to-override-when-creating-a-user-interface-thread"></a>Funciones que se deben reemplazar cuando se crea un subproceso de interfaz de usuario  
  
|Función|Propósito|  
|--------------|-------------|  

|[ExitInstance](../mfc/reference/cwinthread-class.md#exitinstance)| Realizar una limpieza cuando el subproceso termina. Se suele reemplazar. |  
|[InitInstance](../mfc/reference/cwinthread-class.md#initinstance)| Realizar la inicialización de la instancia de subproceso. Se debe invalidar. |  
|[OnIdle](../mfc/reference/cwinthread-class.md#onidle)| Realizar el procesamiento de tiempo de inactividad específicos del subproceso. No se suele reemplazar. |  
|[PreTranslateMessage](../mfc/reference/cwinthread-class.md#pretranslatemessage)| Filtrar los mensajes antes de enviarlos a **TranslateMessage** y **DispatchMessage**. No se suele reemplazar. |  
|[ProcessWndProcException](../mfc/reference/cwinthread-class.md#processwndprocexception)| Interceptar las excepciones no controladas producidas por controladores de mensajes y comandos del subproceso. No se suele reemplazar. |  
|[Ejecutar](../mfc/reference/cwinthread-class.md#run)| Función controladora para el subproceso. Contiene la fuente de mensajes. Casi nunca se reemplaza. |  

  
 MFC proporciona dos versiones de `AfxBeginThread` por medio de sobrecarga de parámetros: una que solo puede crear subprocesos de trabajo y otra que puede crear subprocesos de interfaz de usuario o subprocesos de trabajo. Para iniciar el subproceso de interfaz de usuario, llamar a la segunda sobrecarga de [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), proporcionando la siguiente información:  
  
-   El [RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class) de la clase derivada de `CWinThread`.  
  
-   (Opcional) El nivel de prioridad deseado. El valor predeterminado es la prioridad normal. Para obtener más información acerca de los niveles de prioridad disponibles, vea [SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277) en el [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)].  
  
-   (Opcional) El tamaño de pila deseado para el subproceso. El valor predeterminado para el tamaño de pila es el mismo que el del subproceso creador.  
  
-   (Opcional) **CREATE_SUSPENDED** si desea que el subproceso que se creen en un estado suspendido. El valor predeterminado es 0, es decir, iniciar el subproceso normalmente.  
  
-   (Opcional) Los atributos de seguridad deseados. El valor predeterminado es el mismo acceso que el de su subproceso primario. Para obtener más información acerca del formato de esta información de seguridad, consulte [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) en el [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)].  
  
 `AfxBeginThread` realiza automáticamente la mayoría del trabajo. Crea un nuevo objeto de la clase, lo inicializa con la información suministrada y llama a [CWinThread:: CreateThread](../mfc/reference/cwinthread-class.md#createthread) para empezar a ejecutar el subproceso. Se realizan comprobaciones en todo el procedimiento para asegurar que todos los objetos queden desasignados correctamente en caso de error en algún momento del proceso de creación.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
  
-   [Multithreading: Finalizar subprocesos](../parallel/multithreading-terminating-threads.md)  
  
-   [Multithreading: Crear subprocesos de trabajo](../parallel/multithreading-creating-worker-threads.md)  
  
-   [Procesos y subprocesos](http://msdn.microsoft.com/library/windows/desktop/ms684841)  
  
## <a name="see-also"></a>Vea también  
 [Multithreading con C++ y MFC](../parallel/multithreading-with-cpp-and-mfc.md)