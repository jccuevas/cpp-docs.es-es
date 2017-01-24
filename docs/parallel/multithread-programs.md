---
title: "Programas multiproceso | Microsoft Docs"
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
  - "subprocesamiento múltiple [C++], acerca de los subprocesos"
  - "subprocesamiento [C++], acerca del subprocesamiento"
ms.assetid: 02443596-f7e1-48d0-b3a4-39ee0e54e444
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Programas multiproceso
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un subproceso es, básicamente, un hilo de ejecución dentro de un programa.  Asimismo, es la unidad de ejecución más pequeña que puede programar Win32.  Un subproceso consta de una pila, el estado de los registros de la CPU y una entrada en la lista de ejecución del planificador del sistema.  Cada subproceso comparte todos los recursos del proceso.  
  
 Un proceso consta de uno o varios subprocesos y del código, los datos y otros recursos de un programa en memoria.  Los recursos típicos de un programa son: archivos abiertos, semáforos y memoria asignada dinámicamente.  Un programa se ejecuta cuando el planificador del sistema proporciona el control de la ejecución a uno de los subprocesos.  El planificador determina qué subprocesos deben ejecutarse y cuándo deben hacerlo.  Los subprocesos de baja prioridad quizá deban esperar a que los subprocesos de prioridad más alta completen sus tareas.  En equipos con varios multiprocesadores, el planificador puede ejecutar subprocesos individuales en diferentes procesadores para equilibrar la carga de la CPU.  
  
 Cada subproceso de un proceso funciona de forma independiente.  A menos que se facilite la visibilidad entre subprocesos, éstos se ejecutarán individualmente, sin tener noción de la existencia de otros subprocesos del proceso.  No obstante, los subprocesos que comparten recursos comunes, deben coordinar su trabajo mediante el uso de semáforos u otros métodos de comunicación entre procesos.  Para obtener más información sobre la sincronización de subprocesos, vea [Crear un programa Win32 multiproceso](../parallel/writing-a-multithreaded-win32-program.md).  
  
## Vea también  
 [Subprocesamiento múltiple con C y Win32](../parallel/multithreading-with-c-and-win32.md)