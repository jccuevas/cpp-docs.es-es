---
title: "Compatibilidad del c&#243;digo antiguo con multithreading (Visual C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "programación simultáneo [C++]"
  - "múltiples subprocesos simultáneos"
  - "subprocesos múltiples"
  - "subprocesamiento múltiple [C++]"
  - "subprocesamiento múltiple [C++], acerca del subprocesamiento múltiple"
  - "programación [C++], con subprocesamiento múltiple"
  - "subprocesamiento [C++]"
ms.assetid: 24425b1f-5031-4c6b-aac7-017115a40e7c
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Compatibilidad del c&#243;digo antiguo con multithreading (Visual C++)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ permite ejecutar múltiples subprocesos simultáneos.  Con el multithreading, es posible utilizar tareas que se ejecutan en segundo plano, tratar flujos de entrada simultáneos, administrar interfaces de usuario y muchas otras cosas más.  
  
## En esta sección  
 [Multithreading con C y Win32](../../parallel/multithreading-with-c-and-win32.md)  
 Proporciona compatibilidad para crear aplicaciones multiproceso con Microsoft Windows.  
  
 [Multithreading con C\+\+ y MFC](../../parallel/multithreading-with-cpp-and-mfc.md)  
 Describe qué son los procesos y los subprocesos y cómo trata MFC el multithreading.  
  
 [Subprocesamiento múltiple y configuraciones regionales](../../parallel/multithreading-and-locales.md)  
 Trata problemas que surgen al utilizar la funcionalidad de configuración regional en la biblioteca en tiempo de ejecución C y la biblioteca estándar de C\+\+ en una aplicación multiproceso.  
  
## Secciones relacionadas  
 [CWinThread](../../mfc/reference/cwinthread-class.md)  
 Representa un subproceso de ejecución dentro de una aplicación.  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
 Describe una clase virtual pura que proporciona funcionalidad común para los objetos de sincronización en Win32.  
  
 [CSemaphore](../../mfc/reference/csemaphore-class.md)  
 Representa un semáforo, es decir, un objeto de sincronización que permite que un número limitado de subprocesos de uno o varios procesos tengan acceso a un recurso.  
  
 [CMutex](../../mfc/reference/cmutex-class.md)  
 Representa una exclusión mutua, que es un objeto de sincronización que permite que un subproceso tenga acceso de manera exclusiva mutua a un recurso.  
  
 [CCriticalSection](../../mfc/reference/ccriticalsection-class.md)  
 Representa una sección crítica, que es un objeto de sincronización que permite que sólo un subproceso cada vez tenga acceso a un recurso o sección de código.  
  
 [CEvent](../../mfc/reference/cevent-class.md)  
 Representa un evento, que es un objeto de sincronización que permite que un subproceso notifique a otro que se ha producido un evento.  
  
 [CMultiLock](../../mfc/reference/cmultilock-class.md)  
 Representa el mecanismo de control de acceso utilizado para controlar el acceso a los recursos en un programa de multithreading.  
  
 [CSingleLock](../../mfc/reference/csinglelock-class.md)  
 Representa el mecanismo de control de acceso utilizado para controlar el acceso a un recurso en un programa de multithreading.  
  
 [\(NOTINBUILD\)Visual C\+\+ Programming Methodologies](http://msdn.microsoft.com/es-es/0822f806-fa81-4b65-bf0f-1e2921f30c95)  
 Proporciona vínculos a temas que explican información conceptual sobre las bibliotecas de Visual C\+\+ y temas que tratan diversas tecnologías y técnicas de codificación.