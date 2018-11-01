---
title: Programas multiproceso
ms.date: 11/04/2016
helpviewer_keywords:
- threading [C++], about threading
- multithreading [C++], about threads
ms.assetid: 02443596-f7e1-48d0-b3a4-39ee0e54e444
ms.openlocfilehash: 0b79fe84fbf7d910d53cb5bc333668b7d99ab8ae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502054"
---
# <a name="multithread-programs"></a>Programas multiproceso

Un subproceso es básicamente una ruta de acceso de ejecución a través de un programa. También es la unidad más pequeña de ejecución que programa Win32. Un subproceso consta de una pila, el estado de los registros de la CPU y una entrada en la lista de ejecución del programador del sistema. Cada subproceso comparte todos los recursos del proceso.

Un proceso consta de uno o varios subprocesos y el código, datos y otros recursos de un programa en la memoria. Recursos de programa típicos son archivos abiertos, semáforos y memoria asignada dinámicamente. Un programa se ejecuta cuando el programador del sistema uno de sus subprocesos proporciona control de ejecución. El programador determina qué subprocesos deben ejecutarse y cuándo debe ejecutarse. Subprocesos de baja prioridad es posible que tenga que esperar mientras los subprocesos con prioridad superior completan sus tareas. En equipos con varios procesadores, el programador puede mover los subprocesos individuales en diferentes procesadores para equilibrar la carga de CPU.

Cada subproceso de un proceso funciona de forma independiente. A menos que estén visibles entre sí, los subprocesos se ejecutan por separado y no están conscientes de los demás subprocesos en un proceso. Sin embargo, los subprocesos que comparten recursos comunes, deben coordinar su trabajo mediante el uso de semáforos u otro método de comunicación entre procesos. Para obtener más información acerca de cómo sincronizar los subprocesos, vea [escribiendo un programa Win32 multiproceso](writing-a-multithreaded-win32-program.md).

## <a name="see-also"></a>Vea también

[Multithreading con C y Win32](multithreading-with-c-and-win32.md)