---
title: "Compatibilidad con multithreading código antiguo (Visual C++) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6e082fd9c3f4c34c97f461a11dcec14d778affd8
ms.sourcegitcommit: 185e11ab93af56ffc650fe42fb5ccdf1683e3847
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2018
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
