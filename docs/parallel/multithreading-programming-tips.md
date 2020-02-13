---
title: 'Multithreading: sugerencias de programación para MFC'
ms.date: 08/27/2018
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
ms.openlocfilehash: 79e7d440b478c759c5d4fd683d6af3423e7e8661
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140448"
---
# <a name="multithreading-mfc-programming-tips"></a>Multithreading: sugerencias de programación para MFC

Las aplicaciones multiproceso requieren un mayor cuidado que las aplicaciones de un único subproceso para garantizar que las operaciones se producen en el orden previsto, y que los datos a los que tienen acceso varios subprocesos no están dañados. Este tema describe técnicas para evitar posibles problemas cuando se programan aplicaciones multiproceso con la biblioteca de MFC (Microsoft Foundation Class).

- [Obtener acceso a objetos desde varios subprocesos](#_core_accessing_objects_from_multiple_threads)

- [Obtener acceso a objetos MFC desde subprocesos que no son de MFC](#_core_accessing_mfc_objects_from_non.2d.mfc_threads)

- [Asignaciones de identificadores de Windows](#_core_windows_handle_maps)

- [Comunicación entre subprocesos](#_core_communicating_between_threads)

## <a name="_core_accessing_objects_from_multiple_threads"></a>Obtener acceso a objetos desde varios subprocesos

Los objetos MFC no son seguros para subprocesos por sí mismos. Dos subprocesos independientes no pueden manipular el mismo objeto a menos que use las clases de sincronización de MFC y/o los objetos de sincronización de Win32 adecuados, como las secciones críticas. Para obtener más información sobre las secciones críticas y otros objetos relacionados, vea [Synchronization](/windows/win32/Sync/synchronization) in the Windows SDK.

La biblioteca de clases utiliza internamente secciones críticas para proteger las estructuras de datos globales, como son las utilizadas por la asignación de memoria para depuración.

## <a name="_core_accessing_mfc_objects_from_non.2d.mfc_threads"></a>Obtener acceso a objetos MFC desde subprocesos que no son de MFC

Si tiene una aplicación multiproceso que crea un subproceso de forma distinta a utilizar un objeto [CWinThread](../mfc/reference/cwinthread-class.md) , no puede tener acceso a otros objetos MFC desde ese subproceso. En otras palabras, si desea tener acceso a cualquier objeto MFC desde un subproceso secundario, debe crear ese subproceso con uno de los métodos descritos en [multithreading: crear](multithreading-creating-user-interface-threads.md) subprocesos de interfaz de usuario o [multithreading: crear](multithreading-creating-worker-threads.md)subprocesos de trabajo. Estos métodos son los únicos que permiten a la biblioteca de clases inicializar las variables internas necesarias para controlar aplicaciones multiproceso.

## <a name="_core_windows_handle_maps"></a>Asignaciones de identificadores de Windows

Por regla general, un subproceso sólo puede tener acceso a los objetos MFC que haya creado. Esto se debe a que las asignaciones de identificadores temporales y permanentes de Windows se conservan en almacenamiento local de subprocesos para ayudar a mantener la protección frente a accesos simultáneos desde múltiples subprocesos. Por ejemplo, un subproceso de trabajo no puede realizar un cálculo y entonces llama a la función miembro `UpdateAllViews` de un documento para modificar las ventanas que contienen vistas de los nuevos datos. Esto no tiene ningún efecto, ya que la asignación de `CWnd` objetos a HWND es local en el subproceso principal. Es decir, un subproceso podría tener una asignación de un identificador de Windows a un objeto de C++, pero otro subproceso podría asignar el mismo identificador a un objeto diferente de C++. Los cambios realizados en un subproceso no se reflejarían en el otro.

Existen varias soluciones para este problema. La primera es pasar identificadores individuales (por ejemplo, un HWND) en C++ lugar de objetos al subproceso de trabajo. El subproceso de trabajo agrega entonces estos objetos a su asignación temporal mediante una llamada a la función miembro `FromHandle` apropiada. También puede Agregar el objeto al mapa permanente del subproceso llamando a `Attach`, pero esto solo debe realizarse si se garantiza que el objeto existirá más tiempo que el subproceso.

Otro método consiste en crear nuevos mensajes definidos por el usuario correspondientes a las diferentes tareas que realizarán los subprocesos de trabajo y publicar estos mensajes en la ventana principal de la aplicación mediante `::PostMessage`. Este método de comunicación es similar a dos aplicaciones diferentes que conversan, excepto que ambos subprocesos se ejecutan en el mismo espacio de direcciones.

Para obtener más información sobre las asignaciones de identificadores, vea la [Nota técnica 3](../mfc/tn003-mapping-of-windows-handles-to-objects.md). Para obtener más información sobre el almacenamiento local de subprocesos, vea [almacenamiento local](/windows/win32/ProcThread/thread-local-storage) para el subproceso y [usar el almacenamiento local](/windows/win32/ProcThread/using-thread-local-storage) para el subproceso en el Windows SDK.

## <a name="_core_communicating_between_threads"></a>Comunicación entre subprocesos

MFC proporciona una serie de clases que permiten sincronizar el acceso a los objetos para garantizar subprocesos correctos. El uso de estas clases se describe en [multithreading: uso](multithreading-how-to-use-the-synchronization-classes.md) de las clases de sincronización y [multithreading: Cuándo utilizar las clases de sincronización](multithreading-when-to-use-the-synchronization-classes.md). Para obtener más información sobre estos objetos, vea [Synchronization](/windows/win32/Sync/synchronization) in the Windows SDK.

## <a name="see-also"></a>Consulte también

[Multithreading con C++ y MFC](multithreading-with-cpp-and-mfc.md)
