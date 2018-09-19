---
title: Compatibilidad con multithreading código antiguo (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
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
ms.openlocfilehash: 7b1b301186036460acc07a526267503da8b97678
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/28/2018
ms.locfileid: "43132107"
---
# <a name="multithreading-support-for-older-code-visual-c"></a>Compatibilidad del código antiguo con multithreading (Visual C++)
Visual C++ permite tener varios subprocesos simultáneos de ejecución que se ejecutan simultáneamente. Con subprocesamiento múltiple, puede derivar de tareas en segundo plano, tratar flujos de entrada simultáneos, administrar una interfaz de usuario y mucho más.  
  
## <a name="in-this-section"></a>En esta sección  
 
[Multithreading con C y Win32](multithreading-with-c-and-win32.md)  
Proporciona compatibilidad para crear aplicaciones multiproceso con Microsoft Windows  
  
[Multithreading con C++ y MFC](multithreading-with-cpp-and-mfc.md)  
Describe qué son los procesos y subprocesos y qué enfoque de MFC para multithreading es.  
  
[Multithreading y configuraciones regionales](multithreading-and-locales.md)  
Se describen los problemas que surgen al utilizar la funcionalidad de configuración regional de la biblioteca en tiempo de ejecución de C y la biblioteca estándar de C++ en una aplicación multiproceso.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 
[CWinThread](../mfc/reference/cwinthread-class.md)  
Representa un subproceso de ejecución dentro de una aplicación.  
  
[CSyncObject](../mfc/reference/csyncobject-class.md)  
Describe una clase virtual pura que proporciona funcionalidad común para los objetos de sincronización en Win32.  
  
[CSemaphore](../mfc/reference/csemaphore-class.md)  
Representa un semáforo, que es un objeto de sincronización que permite que un número limitado de subprocesos de uno o varios procesos tengan acceso a un recurso.  
  
[CMutex](../mfc/reference/cmutex-class.md)  
Representa una exclusión mutua, que es un objeto de sincronización que permite que un subproceso tenga acceso de manera exclusiva mutua a un recurso.  
  
[CCriticalSection](../mfc/reference/ccriticalsection-class.md)  
Representa una sección crítica, que es un objeto de sincronización que permite que un subproceso cada vez para tener acceso a un recurso o sección de código.  
  
[CEvent](../mfc/reference/cevent-class.md)  
Representa un evento, que es un objeto de sincronización que permite que un subproceso notifique a otro que se ha producido un evento.  
  
[CMultiLock](../mfc/reference/cmultilock-class.md)  
Representa el mecanismo de control de acceso utilizado para controlar el acceso a los recursos en un programa de multithreading.  
  
[CSingleLock](../mfc/reference/csinglelock-class.md)  
Representa el mecanismo de control de acceso utilizado para controlar el acceso a un recurso en un programa de multithreading.  