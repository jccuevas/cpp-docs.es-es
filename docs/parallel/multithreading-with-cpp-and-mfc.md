---
title: Subprocesamiento múltiple con C++ y MFC | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], multithreading
- threading [C++], MFC
- worker threads [C++]
- synchronization classes [C++]
- synchronization [C++], multithreading
- threading [MFC], about threading
- CWinThread class, purpose of
- multithreading [C++], MFC
- threading [MFC]
- user interface threads [C++]
ms.assetid: 979605f8-3988-44b5-ac9c-b8cce7fcce14
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 778602a0e9236ad8cc788d8a2306e8f2d143ec49
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="multithreading-with-c-and-mfc"></a>Subprocesamiento múltiple con C++ y MFC
La biblioteca (Microsoft Foundation Classes) ofrece compatibilidad con aplicaciones multiproceso. En este tema se describe procesos y subprocesos y el enfoque de MFC multithreading.  
  
 Un proceso es una instancia de ejecución de una aplicación. Por ejemplo, al hacer doble clic en el icono de Bloc de notas, inicie un proceso que se ejecuta el Bloc de notas.  
  
 Un subproceso es una ruta de acceso de ejecución dentro de un proceso. Cuando se inicia el Bloc de notas, el sistema operativo crea un proceso y empieza a ejecutar el subproceso principal de ese proceso. Cuando este subproceso finaliza, por lo que hace el proceso. Este subproceso principal se proporciona para el sistema operativo por el código de inicio en forma de una dirección de función. Por lo general, es la dirección de la **principal** o `WinMain` función que se proporciona.  
  
 Si desea que se puede crear subprocesos adicionales en la aplicación. Puede hacer esto para administrar las tareas de mantenimiento o segundo plano cuando no desea que el usuario espere a que se completen. Todos los subprocesos de aplicaciones MFC se representan mediante [CWinThread](../mfc/reference/cwinthread-class.md) objetos. En la mayoría de los casos, no incluso tiene que crear explícitamente estos objetos; en su lugar, llame a la función auxiliar de framework [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), que crea el `CWinThread` objeto automáticamente.  
  
 MFC distingue entre dos tipos de subprocesos: subprocesos de interfaz de usuario y subprocesos de trabajo. Subprocesos de interfaz de usuario se usan habitualmente para controlar los proporcionados por el usuario y responder a eventos y mensajes generados por el usuario. Subprocesos de trabajo se usan habitualmente para completar tareas, tales como cálculos, que no requieren la intervención del usuario. La API de Win32 no distingue entre tipos de subprocesos; solo necesita conocer la dirección inicial del subproceso para que pueda comenzar a ejecutar el subproceso. MFC controla los subprocesos de interfaz de usuario especialmente proporcionando una bomba de mensaje para los eventos de la interfaz de usuario. `CWinApp` es un ejemplo de un objeto de subproceso de interfaz de usuario, dado que deriva de `CWinThread` y controla los eventos y mensajes generados por el usuario.  
  
 Debe prestarse especial atención a las situaciones donde más de un subproceso puede necesitar acceso al mismo objeto. [Subprocesamiento múltiple: Sugerencias de programación](../parallel/multithreading-programming-tips.md) describen las técnicas que puede usar para solucionar problemas que pueden surgir en estas situaciones. [Subprocesamiento múltiple: Cómo usar las clases de sincronización](../parallel/multithreading-how-to-use-the-synchronization-classes.md) describe cómo utilizar las clases que están disponibles para sincronizar el acceso desde varios subprocesos a un único objeto.  
  
 Escribir y depurar la programación multiproceso son en sí una tarea compleja y difícil, ya que debe asegurarse de que los objetos no tienen acceso varios subprocesos a la vez. Los temas de multithreading no enseña los fundamentos de la programación multiproceso, sino sólo el uso de MFC en el programa de multithreading. Los ejemplos MFC multiproceso incluidos en Visual C++ ilustran algunos multiproceso de agregar funcionalidad y las API de Win32 no contemplados por MFC; Sin embargo, sólo están pensadas para ser un punto de partida.  
  
 Para obtener más información acerca de cómo el sistema operativo trata los procesos y subprocesos, vea [procesos y subprocesos](http://msdn.microsoft.com/library/windows/desktop/ms684841) en el [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)].  
  
 Para obtener más información sobre la compatibilidad con subprocesamiento múltiple de MFC, vea los temas siguientes:  
  
-   [Multithreading: Crear subprocesos de la interfaz de usuario](../parallel/multithreading-creating-user-interface-threads.md)  
  
-   [Multithreading: Crear subprocesos de trabajo](../parallel/multithreading-creating-worker-threads.md)  
  
-   [Multithreading: Uso de las clases de sincronización](../parallel/multithreading-how-to-use-the-synchronization-classes.md)  
  
-   [Multithreading: Finalizar subprocesos](../parallel/multithreading-terminating-threads.md)  
  
-   [Multithreading: Sugerencias de programación](../parallel/multithreading-programming-tips.md)  
  
-   [Multithreading: Cuándo usar las clases de sincronización](../parallel/multithreading-when-to-use-the-synchronization-classes.md)  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad del código antiguo con multithreading (Visual C++)](../parallel/multithreading-support-for-older-code-visual-cpp.md)