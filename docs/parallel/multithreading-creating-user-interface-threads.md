---
title: "Subprocesamiento m&#250;ltiple: Crear subprocesos de la interfaz de usuario | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CREATE_SUSPENDED"
  - "SECURITY_ATTRIBUTES"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "subprocesamiento múltiple [C++], subprocesos de interfaz de usuario"
  - "subprocesamiento [C++], crear subprocesos"
  - "subprocesamiento [C++], subprocesos de interfaz de usuario"
  - "subprocesamiento [MFC], subprocesos de interfaz de usuario"
  - "subprocesos de interfaz de usuario [C++]"
ms.assetid: 446925c1-db59-46ea-ae5b-d5ae5d5b91d8
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Subprocesamiento m&#250;ltiple: Crear subprocesos de la interfaz de usuario
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los subprocesos de interfaz de usuario se utilizan normalmente para controlar los datos proporcionados por el usuario y para responder a los eventos de usuario independientemente de los subprocesos que ejecutan otras partes de la aplicación.  El subproceso principal de la aplicación \(suministrado en la clase derivada de `CWinApp`\) ya está creado y se inicia automáticamente.  Este tema describe los pasos necesarios para crear subprocesos de interfaz de usuario adicionales.  
  
 Lo primero que se debe hacer al crear un subproceso de interfaz de usuario es derivar una clase de [CWinThread](../mfc/reference/cwinthread-class.md).  La clase se debe declarar e implementar mediante las macros [DECLARE\_DYNCREATE](../Topic/DECLARE_DYNCREATE.md) e [IMPLEMENT\_DYNCREATE](../Topic/IMPLEMENT_DYNCREATE.md).  Esta clase debe reemplazar algunas funciones y puede reemplazar otras.  Estas funciones, y su cometido, se presentan en la siguiente tabla.  
  
### Funciones que se deben reemplazar cuando se crea un subproceso de interfaz de usuario  
  
|Función|Objetivo|  
|-------------|--------------|  
|[ExitInstance](../Topic/CWinThread::ExitInstance.md)|Realizar tareas de limpieza cuando el subproceso termina.  Normalmente, se reemplaza.|  
|[InitInstance](../Topic/CWinThread::InitInstance.md)|Llevar a cabo la inicialización de la instancia del subproceso.  Debe reemplazarse.|  
|[OnIdle](../Topic/CWinThread::OnIdle.md)|Realizar el procesamiento de los tiempos de inactividad específicos del subproceso.  No se suele reemplazar.|  
|[PreTranslateMessage](../Topic/CWinThread::PreTranslateMessage.md)|Filtrar los mensajes antes de que se envíen a **TranslateMessage** y **DispatchMessage**.  No se suele reemplazar.|  
|[ProcessWndProcException](../Topic/CWinThread::ProcessWndProcException.md)|Interceptar las excepciones no controladas producidas por el mensaje del subproceso y activar los controladores.  No se suele reemplazar.|  
|[Ejecutar](../Topic/CWinThread::Run.md)|Función controladora para el subproceso.  Contiene la fuente de mensajes.  Casi nunca se reemplaza.|  
  
 MFC proporciona dos versiones de `AfxBeginThread` por medio de sobrecarga de parámetros: una que solo puede crear subprocesos de trabajo y otra que puede crear subprocesos de interfaz de usuario o subprocesos de trabajo.  Para iniciar el subproceso de interfaz de usuario, llame a la segunda sobrecarga de [AfxBeginThread](../Topic/AfxBeginThread.md) con la siguiente información:  
  
-   La [RUNTIME\_CLASS](../Topic/RUNTIME_CLASS.md) de la clase que se derivó de `CWinThread`.  
  
-   \(Opcional\) El nivel de prioridad deseado.  El valor predeterminado es la prioridad normal.  Para obtener más información acerca de los niveles de prioridad disponibles, vea [SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277) en [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)].  
  
-   \(Opcional\) El tamaño de pila deseado para el subproceso.  El valor predeterminado para el tamaño de pila es el mismo que el del subproceso creador.  
  
-   \(Opcional\) **CREATE\_SUSPENDED** si se desea crear el subproceso en el estado suspendido.  El valor predeterminado es 0, es decir, iniciar el subproceso normalmente.  
  
-   \(Opcional\) Los atributos de seguridad deseados.  El valor predeterminado es el mismo acceso que el de su subproceso primario.  Para obtener más información acerca del formato de esta información de seguridad, vea [SECURITY\_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) en [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)].  
  
 `AfxBeginThread` realiza automáticamente la mayoría del trabajo.  Crea un nuevo objeto de la clase, lo inicializa con la información suministrada y llama a [CWinThread::CreateThread](../Topic/CWinThread::CreateThread.md) para empezar a ejecutar el subproceso.  Se realizan comprobaciones en todo el procedimiento para asegurar que todos los objetos queden desasignados correctamente en caso de error en algún momento del proceso de creación.  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Multithreading: Finalizar subprocesos](../parallel/multithreading-terminating-threads.md)  
  
-   [Multithreading: Crear subprocesos de trabajo](../parallel/multithreading-creating-worker-threads.md)  
  
-   [\<caps:sentence id\="tgt49" sentenceid\="d446961ca833a037f83b141ec4859428" class\="tgtSentence"\>Procesos y subprocesos\<\/caps:sentence\>](http://msdn.microsoft.com/library/windows/desktop/ms684841)  
  
## Vea también  
 [Subprocesamiento múltiple con C\+\+ y MFC](../parallel/multithreading-with-cpp-and-mfc.md)