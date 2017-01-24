---
title: "Subprocesamiento m&#250;ltiple con C++ y MFC | Microsoft Docs"
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
  - "CWinThread (clase), finalidad"
  - "MFC [C++], multithreading"
  - "subprocesamiento múltiple [C++], MFC"
  - "sincronización [C++], multithreading"
  - "clases de sincronización [C++]"
  - "subprocesamiento [C++], MFC"
  - "subprocesamiento [MFC]"
  - "subprocesamiento [MFC], acerca del subprocesamiento"
  - "subprocesos de interfaz de usuario [C++]"
  - "subprocesos de trabajo [C++]"
ms.assetid: 979605f8-3988-44b5-ac9c-b8cce7fcce14
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Subprocesamiento m&#250;ltiple con C++ y MFC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La biblioteca de MFC \(Microsoft Foundation Class\) es compatible con aplicaciones multiproceso.  En este tema se describen procesos y subprocesos, así como el enfoque de MFC sobre multithreading.  
  
 Un proceso es una instancia en ejecución de una aplicación.  Por ejemplo, al hacer doble clic en el icono del Bloc de notas, se inicia un proceso que ejecuta el Bloc de notas.  
  
 Un subproceso es una ruta de ejecución dentro de un proceso.  Cuando se inicia el Bloc de notas, el sistema operativo crea un proceso y comienza a ejecutar el subproceso principal de ese proceso.  Cuando este subproceso termina, también lo hace el proceso.  El código de inicio suministra el subproceso principal al sistema operativo en forma de una dirección de función.  Normalmente, es la dirección de la función **main** o `WinMain` la que se suministra.  
  
 Si lo desea, puede crear subprocesos adicionales en la aplicación.  Es recomendable crear estos subprocesos con el fin de tratar tareas en segundo plano o de mantenimiento para las que el usuario no deba esperar a que se completen.  Todos los subprocesos de aplicaciones MFC se representan mediante objetos [CWinThread](../../mfc/reference/cwinthread-class.md).  En la mayoría de los casos, ni siquiera es necesario crear explícitamente estos objetos; en su lugar, basta con llamar a la función auxiliar [AfxBeginThread](../Topic/AfxBeginThread.md) del marco de trabajo, que se encarga de crear el objeto `CWinThread`.  
  
 MFC distingue entre dos tipos de subprocesos: de interfaz de usuario y de trabajo.  Los subprocesos de interfaz de usuario se suelen utilizar para controlar los datos proporcionados por el usuario y para responder a eventos y mensajes generados por el usuario.  Los subprocesos de trabajo se utilizan normalmente para realizar tareas, tales como cálculos, que no requieren que el usuario proporcione datos.  La API Win32 no distingue entre tipos de subprocesos; simplemente, necesita conocer la dirección de inicio del subproceso para poder ejecutarlo.  MFC controla los subprocesos de interfaz de usuario de manera especial proporcionando una serie de mensajes para eventos de la interfaz.  `CWinApp` es un ejemplo de objeto de subproceso de interfaz de usuario, ya que se deriva de `CWinThread` y controla eventos y mensajes generados por el usuario.  
  
 Se debe prestar especial atención a los casos en los que varios subprocesos pueden requerir acceso al mismo objeto.  [Multithreading: Sugerencias de programación](../../parallel/multithreading-programming-tips.md) describe las técnicas que se pueden utilizar para resolver los problemas que pueden surgir en estos casos.  [Multithreading: Uso de las clases de sincronización](../../parallel/multithreading-how-to-use-the-synchronization-classes.md) describe cómo utilizar las clases disponibles para sincronizar el acceso de varios subprocesos a un único objeto.  
  
 La escritura y la depuración de programas multiproceso es, en sí misma, una tarea complicada y difícil, ya que hay que asegurarse de que el acceso a los objetos está limitado a un solo proceso a la vez.  Los temas sobre multithreading no proporcionan la información esencial sobre programación multiproceso, sino sólo el uso de MFC en el programa multiproceso.  Los ejemplos de multiproceso con MFC incluidos en Visual C\+\+ ilustran algunos aspectos de funcionalidad adicional y de bibliotecas API Win32 no contemplados por MFC, sin embargo, sólo pretenden ser un punto de partida.  
  
 Para obtener más información sobre cómo trata el sistema operativo los procesos y subprocesos, vea [Procesos y subprocesos](http://msdn.microsoft.com/library/windows/desktop/ms684841) en [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)].  
  
 Para obtener más información sobre la compatibilidad de MFC con multithreading, vea los siguientes temas:  
  
-   [Multithreading: Crear subprocesos de la interfaz de usuario](../../parallel/multithreading-creating-user-interface-threads.md)  
  
-   [Multithreading: Crear subprocesos de trabajo](../../parallel/multithreading-creating-worker-threads.md)  
  
-   [Multithreading: Uso de las clases de sincronización](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)  
  
-   [Multithreading: Finalizar subprocesos](../../parallel/multithreading-terminating-threads.md)  
  
-   [Multithreading: Sugerencias de programación](../../parallel/multithreading-programming-tips.md)  
  
-   [Multithreading: Cuándo utilizar las clases de sincronización](../../parallel/multithreading-when-to-use-the-synchronization-classes.md)  
  
## Vea también  
 [Compatibilidad del código antiguo con multithreading \(Visual C\+\+\)](../../parallel/multithreading-support-for-older-code-visual-cpp.md)