---
title: 'Multithreading: Sugerencias de programación | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- multithreading [C++], programming tips
- handle maps [C++]
- access control [C++], multithreading
- objects [C++], multiple threads and
- non-MFC threads [C++]
- threading [MFC], programming tips
- critical sections [C++]
- synchronization [C++], multithreading
- programming [C++], multithreaded
- communications [C++], between threads
- threading [C++], best practices
- troubleshooting [C++], multithreading
- Windows handle maps [C++]
ms.assetid: ad14cc70-c91c-4c24-942f-13a75e58bf8a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2ad830117323aef807fcebc1ef61b4dfb1900bd9
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42591316"
---
# <a name="multithreading-programming-tips"></a>Subprocesamiento múltiple: Sugerencias de programación
Las aplicaciones multiproceso requieren un control más estricto que las aplicaciones de un único proceso para el acceso a los datos. Puesto que las aplicaciones multiproceso presentan simultáneamente varios hilos de ejecución independientes, tanto los algoritmos como los datos deben tener en cuenta que los datos pueden ser utilizados por varios procesos al mismo tiempo. Este tema describe técnicas para evitar posibles problemas cuando se programan aplicaciones multiproceso con la biblioteca de MFC (Microsoft Foundation Class).  
  
- [Acceso a objetos desde varios subprocesos](#_core_accessing_objects_from_multiple_threads)  
  
- [Acceso a objetos MFC desde subprocesos no MFC](#_core_accessing_mfc_objects_from_non.2d.mfc_threads)  
  
- [Asignaciones de identificadores de Windows](#_core_windows_handle_maps)  
  
- [Comunicación entre subprocesos](#_core_communicating_between_threads)  
  
##  <a name="_core_accessing_objects_from_multiple_threads"></a> Acceso a objetos desde varios subprocesos  
 
Por motivos de tamaño y rendimiento, los objetos MFC no ofrecen seguridad para subprocesos en el ámbito de los objetos sino sólo en el ámbito de las clases. Esto significa que pueden existir dos subprocesos independientes que manipulen diferentes objetos `CString`, pero no el mismo objeto `CString`. Si es absolutamente necesario disponer de múltiples subprocesos para manipular el mismo objeto, se debe proteger el acceso mediante mecanismos de sincronización de Win32 apropiados como, por ejemplo, secciones críticas. Para obtener más información sobre las secciones críticas y otros objetos relacionados, vea [sincronización](http://msdn.microsoft.com/library/windows/desktop/ms686353) en el SDK de Windows.  
  
La biblioteca de clases utiliza internamente secciones críticas para proteger las estructuras de datos globales, como son las utilizadas por la asignación de memoria para depuración.  
  
##  <a name="_core_accessing_mfc_objects_from_non.2d.mfc_threads"></a> Acceso a objetos MFC desde subprocesos no MFC  
 
Si tiene una aplicación multiproceso que crea un subproceso de forma que no sean un [CWinThread](../mfc/reference/cwinthread-class.md) objeto, no se puede obtener acceso a otros objetos MFC desde ese subproceso. En otras palabras, si desea tener acceso a cualquier objeto MFC desde un subproceso secundario, debe crear ese subproceso con uno de los métodos descritos en [Multithreading: crear subprocesos de la interfaz de usuario](../parallel/multithreading-creating-user-interface-threads.md) o [Multithreading: Crear subprocesos de trabajo](../parallel/multithreading-creating-worker-threads.md). Estos métodos son los únicos que permiten a la biblioteca de clases inicializar las variables internas necesarias para controlar aplicaciones multiproceso.  
  
##  <a name="_core_windows_handle_maps"></a> Asignaciones de identificadores de Windows  
 
Por regla general, un subproceso sólo puede tener acceso a los objetos MFC que haya creado. Esto se debe a que las asignaciones de identificadores temporales y permanentes de Windows se conservan en almacenamiento local para el subproceso para ayudar a mantener la protección frente a accesos simultáneos desde múltiples subproceso. Por ejemplo, un subproceso de trabajo no puede realizar un cálculo y entonces llama a la función miembro `UpdateAllViews` de un documento para modificar las ventanas que contienen vistas de los nuevos datos. Esto no tiene ningún efecto en absoluto, porque la asignación de `CWnd` objetos a los HWND es local para el subproceso principal. Es decir, un subproceso podría tener una asignación de un identificador de Windows a un objeto de C++, pero otro subproceso podría asignar el mismo identificador a un objeto diferente de C++. Los cambios realizados en un subproceso no se reflejarían en el otro.  
  
Existen varias soluciones para este problema. La primera consiste en pasar identificadores individuales (por ejemplo, un HWND) en lugar de los objetos de C++ para el subproceso de trabajo. El subproceso de trabajo agrega entonces estos objetos a su asignación temporal mediante una llamada a la función miembro `FromHandle` apropiada. También podría agregar el objeto a la asignación permanente mediante una llamada a `Attach`, pero esto debe realizarse solo si se garantiza que el objeto sigue existiendo después de los subprocesos.  
  
Otro método consiste en crear mensajes definidos por el usuario correspondientes a las diferentes tareas en los subprocesos de trabajo se realiza y enviar estos mensajes a la ventana principal de la aplicación mediante `::PostMessage`. Este método de comunicación es similar a dos aplicaciones diferentes que conversan, excepto que ambos subprocesos se ejecutan en el mismo espacio de direcciones.  
  
Para obtener más información sobre asignación de identificadores, vea [Nota técnica 3](../mfc/tn003-mapping-of-windows-handles-to-objects.md). Para obtener más información sobre el almacenamiento local de subprocesos, vea [almacenamiento Local de subprocesos](http://msdn.microsoft.com/library/windows/desktop/ms686749) y [utilizar almacenamiento Local de subproceso](http://msdn.microsoft.com/library/windows/desktop/ms686991) en el SDK de Windows.  
  
##  <a name="_core_communicating_between_threads"></a> Comunicación entre subprocesos  
 
MFC proporciona una serie de clases que permiten sincronizar el acceso a los objetos para garantizar subprocesos correctos. Uso de estas clases se describe en [Multithreading: uso de las clases de sincronización](../parallel/multithreading-how-to-use-the-synchronization-classes.md) y [Multithreading: cuándo usar las clases de sincronización](../parallel/multithreading-when-to-use-the-synchronization-classes.md). Para obtener más información acerca de estos objetos, consulte [sincronización](http://msdn.microsoft.com/library/windows/desktop/ms686353) en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  

[Multithreading con C++ y MFC](../parallel/multithreading-with-cpp-and-mfc.md)