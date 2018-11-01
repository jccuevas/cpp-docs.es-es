---
title: Subprocesamiento múltiple con C++ y MFC
ms.date: 08/27/2018
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
ms.openlocfilehash: c707c1c117bbc0005b2b3da4ed39f083ae407b27
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643422"
---
# <a name="multithreading-with-c-and-mfc"></a>Subprocesamiento múltiple con C++ y MFC

La biblioteca Microsoft Foundation Class (MFC) proporciona compatibilidad para aplicaciones multiproceso. En este tema se describe los procesos y subprocesos y el enfoque de MFC sobre multithreading.

Un proceso es una instancia de una aplicación en ejecución. Por ejemplo, al hacer doble clic el icono en el Bloc de notas, se inicia un proceso que se ejecuta el Bloc de notas.

Un subproceso es una ruta de acceso de ejecución dentro de un proceso. Cuando se inicia el Bloc de notas, el sistema operativo crea un proceso y comienza a ejecutarse el subproceso principal de ese proceso. Cuando este subproceso termina, también lo hace el proceso. Este subproceso principal se proporciona al sistema operativo por el código de inicio en forma de una dirección de función. Normalmente, es la dirección de la `main` o `WinMain` función suministrada.

Si desea que puede crear subprocesos adicionales en la aplicación. Es posible que desee hacer esto para controlar tareas en segundo plano o de mantenimiento cuando no desea que el usuario debe esperar a que finalicen. Todos los subprocesos de aplicaciones MFC se representan mediante [CWinThread](../mfc/reference/cwinthread-class.md) objetos. En la mayoría de los casos, no tiene incluso crear explícitamente estos objetos; en su lugar, llame a la función auxiliar de framework [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), que crea el `CWinThread` objeto automáticamente.

MFC distingue entre dos tipos de subprocesos: subprocesos de interfaz de usuario y subprocesos de trabajo. Subprocesos de interfaz de usuario normalmente se usan para controlar la entrada de usuario y responder a eventos y mensajes generados por el usuario. Subprocesos de trabajo se usan habitualmente para completar las tareas, tales como cálculos, que no requieren la intervención del usuario. La API Win32 no distingue entre tipos de subprocesos; solo necesita saber la dirección inicial del subproceso para que pueda comenzar a ejecutar el subproceso. MFC controla los subprocesos de interfaz de usuario de manera especial proporcionando una bomba de mensaje para los eventos de la interfaz de usuario. `CWinApp` es un ejemplo de un objeto de subproceso de interfaz de usuario, porque se deriva de `CWinThread` y controla eventos y mensajes generados por el usuario.

Debe prestarse especial atención a las situaciones donde varios subprocesos pueden requerir acceso al mismo objeto. [Multithreading: Sugerencias de programación](multithreading-programming-tips.md) se describen las técnicas que puede usar para solucionar problemas que pueden surgir en estas situaciones. [Subprocesamiento múltiple: Cómo usar las clases de sincronización](multithreading-how-to-use-the-synchronization-classes.md) describe cómo utilizar las clases que están disponibles para sincronizar el acceso desde varios subprocesos a un único objeto.

Escribir y depurar la programación multiproceso es inherentemente una tarea complicada y difícil, porque debe asegurarse de que los objetos no tienen acceso varios subprocesos a la vez. Los temas sobre multithreading no proporcionan los conceptos básicos de programación multiproceso, solo cómo utilizar MFC en el programa multiproceso. Los ejemplos MFC multiproceso incluidos en Visual C++ ilustran algunos multiproceso de agregar funcionalidad y las API de Win32 no contemplados por MFC; Sin embargo, sólo pretenden ser un punto de partida.

Para obtener más información sobre cómo el sistema operativo controla los procesos y subprocesos, vea [procesos y subprocesos](/windows/desktop/ProcThread/processes-and-threads) en el SDK de Windows.

Para obtener más información sobre la compatibilidad con multithreading de MFC, vea los temas siguientes:

- [Multithreading: Crear subprocesos de la interfaz de usuario](multithreading-creating-user-interface-threads.md)

- [Multithreading: Crear subprocesos de trabajo](multithreading-creating-worker-threads.md)

- [Multithreading: Uso de las clases de sincronización](multithreading-how-to-use-the-synchronization-classes.md)

- [Multithreading: Finalizar subprocesos](multithreading-terminating-threads.md)

- [Multithreading: Sugerencias de programación](multithreading-programming-tips.md)

- [Multithreading: Cuándo usar las clases de sincronización](multithreading-when-to-use-the-synchronization-classes.md)

## <a name="see-also"></a>Vea también

[Compatibilidad del código antiguo con multithreading (Visual C++)](multithreading-support-for-older-code-visual-cpp.md)