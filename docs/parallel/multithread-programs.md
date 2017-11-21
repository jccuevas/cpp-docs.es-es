---
title: Programas multiproceso | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- threading [C++], about threading
- multithreading [C++], about threads
ms.assetid: 02443596-f7e1-48d0-b3a4-39ee0e54e444
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: effbb235ef678253f5258d3eb01a3a82292385cf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="multithread-programs"></a>Programas multiproceso
Un subproceso es básicamente una ruta de acceso de ejecución a través de un programa. También es la unidad más pequeña de ejecución que programa Win32. Un subproceso está compuesto de una pila, el estado de los registros de la CPU y una entrada en la lista de ejecución del programador del sistema. Cada subproceso comparte todos los recursos del proceso.  
  
 Un proceso consta de uno o varios subprocesos y el código, datos y otros recursos de un programa en la memoria. Recursos de programa típicos son archivos abiertos, semáforos y memoria asignada dinámicamente. Un programa se ejecuta cuando el programador del sistema proporciona uno de sus subprocesos de control de la ejecución. El programador determina qué subprocesos deben ejecutarse y cuándo debe ejecutarse. Subprocesos de prioridad más baja que tenga que esperar mientras los subprocesos con prioridad más alta completen sus tareas. En equipos con varios procesadores, el programador puede mover los subprocesos individuales en diferentes procesadores para equilibrar la carga de CPU.  
  
 Cada subproceso de un proceso funciona de forma independiente. A menos que estén visibles entre sí, los subprocesos se ejecutan por separado y no son conscientes de los demás subprocesos en un proceso. Sin embargo, los subprocesos que comparten recursos comunes, deben coordinar su trabajo mediante el uso de semáforos u otro método de comunicación entre procesos. Para obtener más información acerca de cómo sincronizar subprocesos, vea [crear un programa Win32 multiproceso](../parallel/writing-a-multithreaded-win32-program.md).  
  
## <a name="see-also"></a>Vea también  
 [Multithreading con C y Win32](../parallel/multithreading-with-c-and-win32.md)