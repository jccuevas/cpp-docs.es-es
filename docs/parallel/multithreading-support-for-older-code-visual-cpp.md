---
title: Compatibilidad con multithreading código antiguo (Visual C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- threading [C++]
- multiple threads
- concurrent programming [C++]
- programming [C++], multithreaded
- multithreading [C++], about multithreading
- multiple concurrent threads
- multithreading [C++]
ms.assetid: 24425b1f-5031-4c6b-aac7-017115a40e7c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b4ecd5f210aa01c41b3806ce15e19e77b8c93324
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687730"
---
# <a name="multithreading-support-for-older-code-visual-c"></a>Compatibilidad del código antiguo con multithreading (Visual C++)
Visual C++ permite tener varios subprocesos simultáneos de ejecución que se ejecutan simultáneamente. Con subprocesamiento múltiple, puede utilizar tareas en segundo plano, administrar flujos de entrada simultáneos, administrar una interfaz de usuario y mucho más.  
  
## <a name="in-this-section"></a>En esta sección  
 [Multithreading con C y Win32](../parallel/multithreading-with-c-and-win32.md)  
 Proporciona compatibilidad para crear aplicaciones multiproceso con Microsoft Windows  
  
 [Multithreading con C++ y MFC](../parallel/multithreading-with-cpp-and-mfc.md)  
 Describe los procesos y subprocesos, y qué método la MFC para subprocesamiento múltiple es.  
  
 [Multithreading y configuraciones regionales](../parallel/multithreading-and-locales.md)  
 Describe los problemas que surgen al utilizar la funcionalidad de configuración regional de la biblioteca en tiempo de ejecución de C y la biblioteca estándar de C++ en una aplicación multiproceso.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [CWinThread](../mfc/reference/cwinthread-class.md)  
 Representa un subproceso de ejecución dentro de una aplicación.  
  
 [CSyncObject](../mfc/reference/csyncobject-class.md)  
 Describe una clase virtual pura que proporciona funcionalidad común para los objetos de sincronización en Win32.  
  
 [CSemaphore](../mfc/reference/csemaphore-class.md)  
 Representa un semáforo, que es un objeto de sincronización que permite a un número limitado de subprocesos de uno o varios procesos tengan acceso a un recurso.  
  
 [CMutex](../mfc/reference/cmutex-class.md)  
 Representa una exclusión mutua, que es un objeto de sincronización que permite que un subproceso tenga acceso de manera exclusiva mutua a un recurso.  
  
 [CCriticalSection](../mfc/reference/ccriticalsection-class.md)  
 Representa una sección crítica, que es un objeto de sincronización que permite que un subproceso a la vez para tener acceso a un recurso o sección de código.  
  
 [CEvent](../mfc/reference/cevent-class.md)  
 Representa un evento, que es un objeto de sincronización que permite que un subproceso notifique a otro que se ha producido un evento.  
  
 [CMultiLock](../mfc/reference/cmultilock-class.md)  
 Representa el mecanismo de control de acceso utilizado para controlar el acceso a los recursos en un programa de multithreading.  
  
 [CSingleLock](../mfc/reference/csinglelock-class.md)  
 Representa el mecanismo de control de acceso utilizado para controlar el acceso a un recurso en un programa de multithreading.  
