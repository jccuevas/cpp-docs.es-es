---
title: "Subprocesamiento m&#250;ltiple: Sugerencias de programaci&#243;n | Microsoft Docs"
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
  - "control de acceso [C++], multithreading"
  - "comunicaciones [C++], entre subprocesos"
  - "secciones críticas [C++]"
  - "asignaciones de identificadores [C++]"
  - "subprocesamiento múltiple [C++], sugerencias de programación"
  - "subprocesos no MFC [C++]"
  - "objetos [C++], subprocesos múltiples y"
  - "programación [C++], con subprocesamiento múltiple"
  - "sincronización [C++], multithreading"
  - "subprocesamiento [C++], procedimientos recomendados"
  - "subprocesamiento [MFC], sugerencias de programación"
  - "solucionar problemas [C++], multithreading"
  - "asignaciones de identificadores de Windows [C++]"
ms.assetid: ad14cc70-c91c-4c24-942f-13a75e58bf8a
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Subprocesamiento m&#250;ltiple: Sugerencias de programaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las aplicaciones multiproceso requieren un control más estricto que las aplicaciones de un único proceso para el acceso a los datos.  Puesto que las aplicaciones multiproceso presentan simultáneamente varios hilos de ejecución independientes, tanto los algoritmos como los datos deben tener en cuenta que los datos pueden ser utilizados por varios procesos al mismo tiempo.  Este tema describe técnicas para evitar posibles problemas cuando se programan aplicaciones multiproceso con la biblioteca de MFC \(Microsoft Foundation Class\).  
  
-   [Acceso a objetos desde múltiples subprocesos](#_core_accessing_objects_from_multiple_threads)  
  
-   [Acceso a objetos MFC desde subprocesos no MFC](#_core_accessing_mfc_objects_from_non.2d.mfc_threads)  
  
-   [Asignaciones de identificadores de Windows](#_core_windows_handle_maps)  
  
-   [Comunicación entre subprocesos](#_core_communicating_between_threads)  
  
##  <a name="_core_accessing_objects_from_multiple_threads"></a> Acceso a objetos desde múltiples subprocesos  
 Por motivos de tamaño y rendimiento, los objetos MFC no ofrecen seguridad para subprocesos en el ámbito de los objetos sino sólo en el ámbito de las clases.  Esto significa que pueden existir dos subprocesos independientes que manipulen diferentes objetos `CString`, pero no el mismo objeto `CString`.  Si es absolutamente necesario disponer de múltiples subprocesos para manipular el mismo objeto, se debe proteger el acceso mediante mecanismos de sincronización de Win32 apropiados como, por ejemplo, secciones críticas.  Para obtener más información acerca de las secciones críticas y otros objetos relacionados, vea [Sincronización](http://msdn.microsoft.com/library/windows/desktop/ms686353) en [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)].  
  
 La biblioteca de clases utiliza internamente secciones críticas para proteger las estructuras de datos globales, como son las utilizadas por la asignación de memoria para depuración.  
  
##  <a name="_core_accessing_mfc_objects_from_non.2d.mfc_threads"></a> Acceso a objetos MFC desde subprocesos no MFC  
 En una aplicación multiproceso que crea un subproceso sin utilizar un objeto [CWinThread](../mfc/reference/cwinthread-class.md), no es posible tener acceso a otros objetos MFC desde ese subproceso.  Es decir, si desea tener acceso a cualquier objeto MFC desde un subproceso secundario, debe crear ese subproceso con uno de los métodos descritos en [Multithreading: Crear subprocesos de la interfaz de usuario](../parallel/multithreading-creating-user-interface-threads.md) o [Multithreading: Crear subprocesos de trabajo](../parallel/multithreading-creating-worker-threads.md).  Estos métodos son los únicos que permiten a la biblioteca de clases inicializar las variables internas necesarias para controlar aplicaciones multiproceso.  
  
##  <a name="_core_windows_handle_maps"></a> Asignaciones de identificadores de Windows  
 Por regla general, un subproceso sólo puede tener acceso a los objetos MFC que haya creado.  Esto se debe a que las asignaciones de identificadores temporales y permanentes de Windows se conservan en almacenamiento local de subprocesos para ayudar a mantener la protección frente a accesos simultáneos desde múltiples subprocesos.  Por ejemplo, un subproceso de trabajo no puede realizar un cálculo y entonces llama a la función miembro `UpdateAllViews` de un documento para modificar las ventanas que contienen vistas de los nuevos datos.  Esto no tiene ningún efecto, ya que la asignación de objetos `CWnd` a identificadores `HWND` es local en relación con el subproceso primario.  Es decir, un subproceso podría tener una asignación de un identificador de Windows a un objeto de C\+\+, pero otro subproceso podría asignar el mismo identificador a un objeto diferente de C\+\+.  Los cambios realizados en un subproceso no se reflejarían en el otro.  
  
 Existen varias soluciones para este problema.  La primera consiste en pasar identificadores individuales \(tales como un `HWND`\), en vez de objetos de C\+\+, al subproceso de trabajo.  El subproceso de trabajo agrega entonces estos objetos a su asignación temporal mediante una llamada a la función miembro `FromHandle` apropiada.  También se podría agregar el objeto a la asignación permanente mediante una llamada a **Attach**, pero esto sólo se debería hacer si se tiene la garantía de que el objeto sigue existiendo después de terminar el subproceso.  
  
 Otro método consiste en crear mensajes definidos por el usuario correspondientes a las diferentes tareas que el subproceso de trabajo vaya a realizar, y enviar estos mensajes a la ventana principal de la aplicación mediante **::PostMessage**.  Este método de comunicación es similar a dos aplicaciones diferentes que conversan, excepto que ambos subprocesos se ejecutan en el mismo espacio de direcciones.  
  
 Para obtener más información sobre asignación de identificadores, vea la [Nota técnica 3](../mfc/tn003-mapping-of-windows-handles-to-objects.md).  Para obtener más información sobre el almacenamiento local de subprocesos, vea [Almacenamiento local de subprocesos \(TLS\)](http://msdn.microsoft.com/library/windows/desktop/ms686749) y [Utilizar almacenamiento local de subprocesos](http://msdn.microsoft.com/library/windows/desktop/ms686991) en [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)].  
  
##  <a name="_core_communicating_between_threads"></a> Comunicación entre subprocesos  
 MFC proporciona una serie de clases que permiten sincronizar el acceso a los objetos para garantizar subprocesos correctos.  La utilización de estas clases se describe en [Multithreading: Uso de las clases de sincronización](../parallel/multithreading-how-to-use-the-synchronization-classes.md) y [Multithreading: Cuándo utilizar las clases de sincronización](../parallel/multithreading-when-to-use-the-synchronization-classes.md).  Para obtener más información sobre estos objetos, vea [Sincronización](http://msdn.microsoft.com/library/windows/desktop/ms686353) en [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)].  
  
## Vea también  
 [Subprocesamiento múltiple con C\+\+ y MFC](../parallel/multithreading-with-cpp-and-mfc.md)