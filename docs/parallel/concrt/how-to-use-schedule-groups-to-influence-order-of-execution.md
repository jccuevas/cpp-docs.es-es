---
title: 'Cómo: usar grupos de programación para influir en el orden de ejecución | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- schedule groups, using [Concurrency Runtime]
- using schedule groups [Concurrency Runtime]
ms.assetid: 73124194-fc3a-491e-a23f-fbd7b5a4455c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 55417f1d72d6bd3e111a89f4b28f783543101b6e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415881"
---
# <a name="how-to-use-schedule-groups-to-influence-order-of-execution"></a>Cómo: Usar grupos de programación para influir en el orden de ejecución

En el Runtime de simultaneidad, el orden en el que se programan las tareas no es determinista. Sin embargo, puede utilizar directivas de programación para influir en el orden en el que se ejecutan las tareas. En este tema se muestra cómo usar grupos de programación junto con el [Concurrency:: SchedulingProtocol](reference/concurrency-namespace-enums.md#policyelementkey) directiva de programador para influir en el orden en que se ejecutan las tareas.

En el ejemplo se ejecuta un conjunto de tareas dos veces, cada una con una directiva de programación diferente. Ambas directivas limitan el número máximo de recursos de procesamiento a dos. La primera ejecución usa la `EnhanceScheduleGroupLocality` directiva, que es el valor predeterminado y la segunda serie usa el `EnhanceForwardProgress` directiva. Con la directiva `EnhanceScheduleGroupLocality`, el programador ejecuta todas las tareas de un grupo de programación hasta que todas las tareas finalizan o dan paso a otra. Con la directiva `EnhanceForwardProgress`, el programador se mueve al siguiente grupo de programación en un comportamiento por turnos inmediatamente después de que una tarea finaliza o produce un resultado.

Cuando cada grupo de programación contiene tareas relacionadas, la directiva `EnhanceScheduleGroupLocality` suele suponer una mejora en el rendimiento, ya que el emplazamiento en caché se conserva entre las tareas. La directiva `EnhanceForwardProgress` permite a las tareas progresar y es útil cuando se precisa equidad de programación entre los grupos de programación.

## <a name="example"></a>Ejemplo

Este ejemplo se define la `work_yield_agent` (clase), que se deriva de [Concurrency:: Agent](../../parallel/concrt/reference/agent-class.md). La clase `work_yield_agent` realiza una unidad de trabajo, produce el contexto actual y, a continuación, realiza otra unidad de trabajo. El agente utiliza el [Concurrency:: wait](reference/concurrency-namespace-functions.md#wait) función para ceder de forma cooperativa el contexto actual para que pueden ejecutar otros contextos.

En este ejemplo se crean cuatro objetos `work_yield_agent`. Para mostrar cómo establecer directivas del programador para incluir en el orden en que se ejecutan los agentes, el ejemplo asocia los dos primeros agentes a un grupo de programación y los otros dos a otro. El ejemplo se usa el [concurrency::CurrentScheduler::CreateScheduleGroup](reference/currentscheduler-class.md#createschedulegroup) método para crear el [Concurrency:: ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) objetos. En el ejemplo se ejecutan los cuatro agentes dos veces, cada vez que con una directiva de programación diferente.

[!code-cpp[concrt-scheduling-protocol#1](../../parallel/concrt/codesnippet/cpp/how-to-use-schedule-groups-to-influence-order-of-execution_1.cpp)]

Este ejemplo produce el siguiente resultado:

```Output
Using EnhanceScheduleGroupLocality...
group 0,
    task 0: first loop...
group 0,
    task 1: first loop...
group 0,
    task 0: waiting...
group 1,
    task 0: first loop...
group 0,
    task 1: waiting...
group 1,
    task 1: first loop...
group 1,
    task 0: waiting...
group 0,
    task 0: second loop...
group 1,
    task 1: waiting...
group 0,
    task 1: second loop...
group 0,
    task 0: finished...
group 1,
    task 0: second loop...
group 0,
    task 1: finished...
group 1,
    task 1: second loop...
group 1,
    task 0: finished...
group 1,
    task 1: finished...

Using EnhanceForwardProgress...
group 0,
    task 0: first loop...
group 1,
    task 0: first loop...
group 0,
    task 0: waiting...
group 0,
    task 1: first loop...
group 1,
    task 0: waiting...
group 1,
    task 1: first loop...
group 0,
    task 1: waiting...
group 0,
    task 0: second loop...
group 1,
    task 1: waiting...
group 1,
    task 0: second loop...
group 0,
    task 0: finished...
group 0,
    task 1: second loop...
group 1,
    task 0: finished...
group 1,
    task 1: second loop...
group 0,
    task 1: finished...
group 1,
    task 1: finished...
```

Ambas directivas producen la misma secuencia de eventos. Sin embargo, la directiva que utiliza `EnhanceScheduleGroupLocality` inicia los dos agentes que forman parte del primer grupo de programación antes de iniciar los agentes que forman parte del segundo grupo. La directiva que utiliza `EnhanceForwardProgress` inicia un agente del primer grupo y, a continuación, inicia el primer agente del segundo grupo.

## <a name="compiling-the-code"></a>Compilar el código

Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `scheduling-protocol.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

**cl.exe/EHsc scheduling-protocol.cpp**

## <a name="see-also"></a>Vea también

[Grupos de programación](../../parallel/concrt/schedule-groups.md)<br/>
[Agentes asincrónicos](../../parallel/concrt/asynchronous-agents.md)

