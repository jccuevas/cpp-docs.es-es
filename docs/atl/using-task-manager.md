---
title: "Using Task Manager | Microsoft Docs"
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
  - "puntos de interrupción, Task Manager"
  - "depurar [ATL], using Task Manager"
  - "Task Manager"
ms.assetid: 773fccd5-308d-42c2-a17f-60ae94989062
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Using Task Manager
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una de las maneras más fácil de depurar un servicio es utilizar el administrador de tareas de Windows NT 4.0 o Windows 2000.  Mientras se ejecuta el servicio, inicie el administrador de tareas y haga clic en la ficha de **Procesos** .  Haga clic con el botón secundario en el nombre del archivo EXE y haga clic en **Depurar**.  Esto inicia Visual C\+\+ asociado a ese proceso en ejecución.  Ahora, haga clic **Inter** en el menú de **Depurar** para permitir que se establezca puntos de interrupción en el código.  Haga clic en **Ejecutar** para ejecutarse a los puntos de interrupción seleccionados.  
  
## Vea también  
 [Debugging Tips](../atl/debugging-tips.md)