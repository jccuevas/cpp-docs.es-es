---
title: "C&#243;mo: Usar grupos de programaci&#243;n para influir en el orden de ejecuci&#243;n | Microsoft Docs"
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
  - "grupos de programación, usar [Runtime de simultaneidad]"
  - "usar grupos de programación [Runtime de simultaneidad]"
ms.assetid: 73124194-fc3a-491e-a23f-fbd7b5a4455c
caps.latest.revision: 15
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Usar grupos de programaci&#243;n para influir en el orden de ejecuci&#243;n
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En el Runtime de simultaneidad, el orden en el que se programan las tareas no es determinista.  Sin embargo, puede utilizar directivas de programación para influir en el orden en el que se ejecutan las tareas.  En este tema se muestra cómo usar grupos de programación junto con la directiva de programador [concurrency::SchedulingProtocol](../Topic/PolicyElementKey%20Enumeration.md) para influir en el orden en que se ejecutan las tareas.  
  
 En el ejemplo se ejecuta un conjunto de tareas dos veces, cada una con una directiva de programación diferente.  Ambas directivas limitan el número máximo de recursos de procesamiento a dos.  La primera ejecución usa la directiva `EnhanceScheduleGroupLocality` \(el valor predeterminado\) y la segunda usa la directiva `EnhanceForwardProgress`.  Con la directiva `EnhanceScheduleGroupLocality`, el programador ejecuta todas las tareas de un grupo de programación hasta que todas las tareas finalizan o dan paso a otra.  Con la directiva `EnhanceForwardProgress`, el programador se mueve al siguiente grupo de programación en un comportamiento por turnos inmediatamente después de que una tarea finaliza o produce un resultado.  
  
 Cuando cada grupo de programación contiene tareas relacionadas, la directiva `EnhanceScheduleGroupLocality` suele suponer una mejora en el rendimiento, ya que el emplazamiento en caché se conserva entre las tareas.  La directiva `EnhanceForwardProgress` permite a las tareas progresar y es útil cuando se precisa equidad de programación entre los grupos de programación.  
  
## Ejemplo  
 En este ejemplo se define la clase `work_yield_agent`, que se deriva de [concurrency::agent](../../parallel/concrt/reference/agent-class.md).  La clase `work_yield_agent` realiza una unidad de trabajo, produce el contexto actual y, a continuación, realiza otra unidad de trabajo.  El agente emplea la función [concurrency::wait](../Topic/wait%20Function.md) para ceder de forma cooperativa el contexto actual, de forma que se puedan ejecutar otros contextos.  
  
 En este ejemplo se crean cuatro objetos `work_yield_agent`.  Para mostrar cómo establecer directivas del programador para incluir en el orden en que se ejecutan los agentes, el ejemplo asocia los dos primeros agentes a un grupo de programación y los otros dos a otro.  En el ejemplo se usa el método [concurrency::CurrentScheduler::CreateScheduleGroup](../Topic/CurrentScheduler::CreateScheduleGroup%20Method.md) para crear los objetos [concurrency::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md).  En el ejemplo se ejecutan los cuatro agentes dos veces, cada vez que con una directiva de programación diferente.  
  
 [!code-cpp[concrt-scheduling-protocol#1](../../parallel/concrt/codesnippet/CPP/how-to-use-schedule-groups-to-influence-order-of-execution_1.cpp)]  
  
 Este ejemplo produce el siguiente resultado:  
  
  **Using EnhanceScheduleGroupLocality...**  
**group 0,task 0: first loop...**  
**group 0,task 1: first loop...**  
**group 0,task 0: waiting...**  
**group 1,task 0: first loop...**  
**group 0,task 1: waiting...**  
**group 1,task 1: first loop...**  
**group 1,task 0: waiting...**  
**group 0,task 0: second loop...**  
**group 1,task 1: waiting...**  
**group 0,task 1: second loop...**  
**group 0,task 0: finished...**  
**group 1,task 0: second loop...**  
**group 0,task 1: finished...**  
**group 1,task 1: second loop...**  
**group 1,task 0: finished...**  
**group 1,task 1: finished...**  
**Using EnhanceForwardProgress...**  
**group 0,task 0: first loop...**  
**group 1,task 0: first loop...**  
**group 0,task 0: waiting...**  
**group 0,task 1: first loop...**  
**group 1,task 0: waiting...**  
**group 1,task 1: first loop...**  
**group 0,task 1: waiting...**  
**group 0,task 0: second loop...**  
**group 1,task 1: waiting...**  
**group 1,task 0: second loop...**  
**group 0,task 0: finished...**  
**group 0,task 1: second loop...**  
**group 1,task 0: finished...**  
**group 1,task 1: second loop...**  
**group 0,task 1: finished...**  
**group 1,task 1: finished...** Ambas directivas producen la misma secuencia de eventos.  Sin embargo, la directiva que utiliza `EnhanceScheduleGroupLocality` inicia los dos agentes que forman parte del primer grupo de programación antes de iniciar los agentes que forman parte del segundo grupo.  La directiva que utiliza `EnhanceForwardProgress` inicia un agente del primer grupo y, a continuación, inicia el primer agente del segundo grupo.  
  
## Compilar el código  
 Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o en un archivo denominado `scheduling-protocol.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.  
  
 **cl.exe \/EHsc scheduling\-protocol.cpp**  
  
## Vea también  
 [Grupos de programación](../../parallel/concrt/schedule-groups.md)   
 [Agentes asincrónicos](../../parallel/concrt/asynchronous-agents.md)