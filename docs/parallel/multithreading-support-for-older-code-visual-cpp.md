---
title: Compatibilidad del código antiguo con multithreading (Visual C++)
ms.date: 08/27/2018
helpviewer_keywords:
- threading [C++]
- multiple threads
- concurrent programming [C++]
- programming [C++], multithreaded
- multithreading [C++], about multithreading
- multiple concurrent threads
- multithreading [C++]
ms.assetid: 24425b1f-5031-4c6b-aac7-017115a40e7c
ms.openlocfilehash: 649e26c3f0704dfd6740b1a250613545e29316a3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407749"
---
# <a name="multithreading-support-for-older-code-visual-c"></a>Compatibilidad del código antiguo con multithreading (Visual C++)

Visual C++ permite tener varios subprocesos simultáneos de ejecución que se ejecutan simultáneamente. Con subprocesamiento múltiple, puede derivar de tareas en segundo plano, tratar flujos de entrada simultáneos, administrar una interfaz de usuario y mucho más.

## <a name="in-this-section"></a>En esta sección

[Multithreading con C y Win32](multithreading-with-c-and-win32.md)<br/>
Proporciona compatibilidad para crear aplicaciones multiproceso con Microsoft Windows

[Multithreading con C++ y MFC](multithreading-with-cpp-and-mfc.md)<br/>
Describe qué son los procesos y subprocesos y qué enfoque de MFC para multithreading es.

[Multithreading y configuraciones regionales](multithreading-and-locales.md)<br/>
Se describen los problemas que surgen al utilizar la funcionalidad de configuración regional de la biblioteca en tiempo de ejecución de C y la biblioteca estándar de C++ en una aplicación multiproceso.

## <a name="related-sections"></a>Secciones relacionadas

[CWinThread](../mfc/reference/cwinthread-class.md)<br/>
Representa un subproceso de ejecución dentro de una aplicación.

[CSyncObject](../mfc/reference/csyncobject-class.md)<br/>
Describe una clase virtual pura que proporciona funcionalidad común para los objetos de sincronización en Win32.

[CSemaphore](../mfc/reference/csemaphore-class.md)<br/>
Representa un semáforo, que es un objeto de sincronización que permite que un número limitado de subprocesos de uno o varios procesos tengan acceso a un recurso.

[CMutex](../mfc/reference/cmutex-class.md)<br/>
Representa una exclusión mutua, que es un objeto de sincronización que permite que un subproceso tenga acceso de manera exclusiva mutua a un recurso.

[CCriticalSection](../mfc/reference/ccriticalsection-class.md)<br/>
Representa una sección crítica, que es un objeto de sincronización que permite que un subproceso cada vez para tener acceso a un recurso o sección de código.

[CEvent](../mfc/reference/cevent-class.md)<br/>
Representa un evento, que es un objeto de sincronización que permite que un subproceso notifique a otro que se ha producido un evento.

[CMultiLock](../mfc/reference/cmultilock-class.md)<br/>
Representa el mecanismo de control de acceso utilizado para controlar el acceso a los recursos en un programa de multithreading.

[CSingleLock](../mfc/reference/csinglelock-class.md)<br/>
Representa el mecanismo de control de acceso utilizado para controlar el acceso a un recurso en un programa de multithreading.