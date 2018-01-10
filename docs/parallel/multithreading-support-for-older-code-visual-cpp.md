---
title: "Compatibilidad con multithreading código antiguo (Visual C++) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- threading [C++]
- multiple threads
- concurrent programming [C++]
- programming [C++], multithreaded
- multithreading [C++], about multithreading
- multiple concurrent threads
- multithreading [C++]
ms.assetid: 24425b1f-5031-4c6b-aac7-017115a40e7c
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1037b8b81c9286ac1b1dd9303294b4300e7c9309
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
  
 [(NOTINBUILD) Metodologías de programación de Visual C++](http://msdn.microsoft.com/en-us/0822f806-fa81-4b65-bf0f-1e2921f30c95)  
 Proporciona vínculos a temas que proporcionan información conceptual sobre las bibliotecas de Visual C++ y temas que tratan diversas tecnologías y técnicas de codificación.