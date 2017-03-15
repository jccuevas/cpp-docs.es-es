---
title: "Displaying Assertions | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aserciones, depurar"
  - "aserciones, mostrar"
  - "depurar [ATL], displaying assertions"
  - "depurar aserciones"
ms.assetid: fa353fe8-4656-4384-a5d2-8866bc977f06
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Displaying Assertions
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si el cliente conectado al servicio aparece deje de responder, el servicio puede haber contendido y enviarse un cuadro de mensaje que no puede ver.  Puede confirmar esto con el depurador de Visual C\+\+ para depurar el código \(vea [Mediante el administrador de tareas](../atl/using-task-manager.md) anteriormente en esta sección\).  
  
 Si determina que el servicio muestra un cuadro de mensaje que no puede ver, puede establecer la opción de **Permitir que el servicio interactúe con el equipo** antes de utilizar el servicio de nuevo.  Esta opción es un parámetro de inicio permite que cualquier cuadro de mensaje mostrado por el servicio para aparecer en el escritorio.  Para establecer esta opción, abra la aplicación del Panel de control de Servicios, seleccione el servicio, haga clic en **Inicio**, y seleccione la opción de **Permitir que el servicio interactúe con el equipo** .  
  
## Vea también  
 [Debugging Tips](../atl/debugging-tips.md)