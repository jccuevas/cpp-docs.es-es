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
ms.openlocfilehash: eaf28404b06e9b0bf6126d8bbc140bf46cff37da
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512016"
---
# <a name="multithreading-with-c-and-mfc"></a>Subprocesamiento múltiple con C++ y MFC

La biblioteca MFC (Microsoft Foundation Class) proporciona compatibilidad con aplicaciones multiproceso. En este tema se describen los procesos y subprocesos y el enfoque de MFC para multithreading.

Un proceso es una instancia en ejecución de una aplicación. Por ejemplo, al hacer doble clic en el icono del Bloc de notas, inicia un proceso que ejecuta el Bloc de notas.

Un subproceso es una ruta de ejecución dentro de un proceso. Al iniciar el Bloc de notas, el sistema operativo crea un proceso y comienza a ejecutar el subproceso principal de ese proceso. Cuando este subproceso finaliza, se realiza el proceso. El código de inicio proporciona este subproceso principal al sistema operativo en forma de dirección de función. Normalmente, es la dirección de la `main` función o `WinMain` que se proporciona.

Si lo desea, puede crear subprocesos adicionales en la aplicación. Puede que desee hacer esto para controlar las tareas de fondo o mantenimiento cuando no desea que el usuario espere a que se completen. Todos los subprocesos de las aplicaciones MFC se representan mediante objetos [CWinThread](../mfc/reference/cwinthread-class.md) . En la mayoría de los casos, ni siquiera es necesario crear explícitamente estos objetos; en su lugar, llame a la función auxiliar de Framework [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread), `CWinThread` que crea el objeto automáticamente.

MFC distingue dos tipos de subprocesos: subprocesos de la interfaz de usuario y subprocesos de trabajo. Los subprocesos de la interfaz de usuario se utilizan normalmente para controlar los datos proporcionados por el usuario y responder a eventos y mensajes generados por el usuario. Los subprocesos de trabajo se utilizan normalmente para completar tareas, como el recálculo, que no requieren la intervención del usuario. La API de Win32 no distingue entre tipos de subprocesos; solo debe conocer la dirección de inicio del subproceso para que pueda empezar a ejecutar el subproceso. MFC controla los subprocesos de la interfaz de usuario de forma especial proporcionando un bombeo de mensajes para los eventos en la interfaz de usuario. `CWinApp`es un ejemplo de un objeto de subproceso de interfaz de usuario, porque deriva `CWinThread` de y controla eventos y mensajes generados por el usuario.

Se debe prestar especial atención a situaciones en las que más de un subproceso pueda requerir acceso al mismo objeto. [Multithreading: Sugerencias](multithreading-programming-tips.md) de programación describe las técnicas que puede usar para solucionar los problemas que puedan surgir en estas situaciones. [Multithreading: Cómo usar las clases](multithreading-how-to-use-the-synchronization-classes.md) de sincronización describe cómo utilizar las clases que están disponibles para sincronizar el acceso desde varios subprocesos a un único objeto.

Escribir y depurar la programación multiproceso es intrínsecamente una tarea complicada y difícil, ya que debe asegurarse de que más de un subproceso tenga acceso a los objetos a la vez. Los temas de multithreading no enseñan los aspectos básicos de la programación multiproceso, solo cómo usar MFC en el programa multiproceso. Los ejemplos de MFC multiproceso incluidos en Visual C++ ilustran una serie de funciones de adición multiproceso y API de Win32 no incluidas en MFC; sin embargo, solo están pensados para ser un punto de partida.

Para obtener más información sobre cómo el sistema operativo controla los procesos y los subprocesos, vea [procesos y](/windows/win32/ProcThread/processes-and-threads) subprocesos en el Windows SDK.

Para obtener más información acerca de la compatibilidad con multithreading de MFC, vea los temas siguientes:

- [Multithreading: crear subprocesos de interfaz de usuario](multithreading-creating-user-interface-threads.md)

- [Multithreading: crear subprocesos de trabajo](multithreading-creating-worker-threads.md)

- [Multithreading: cómo usar las clases de sincronización](multithreading-how-to-use-the-synchronization-classes.md)

- [Multithreading: terminar subprocesos](multithreading-terminating-threads.md)

- [Multithreading: sugerencias de programación](multithreading-programming-tips.md)

- [Multithreading: cuándo usar las clases de sincronización](multithreading-when-to-use-the-synchronization-classes.md)

## <a name="see-also"></a>Vea también

[Compatibilidad del código antiguo con multithreading (Visual C++)](multithreading-support-for-older-code-visual-cpp.md)
