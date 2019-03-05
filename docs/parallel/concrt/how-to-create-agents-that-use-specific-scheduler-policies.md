---
title: Procedimiento Crear a agentes que usen directivas de programador específicas
ms.date: 11/04/2016
helpviewer_keywords:
- scheduler policies, agents [Concurrency Runtime]
- creating agents that use specific policies [Concurrency Runtime]
ms.assetid: 46a3e265-0777-4ec3-a142-967bafc49d67
ms.openlocfilehash: 5aac86801015549b5552b51c06a30f8398346a06
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57257376"
---
# <a name="how-to-create-agents-that-use-specific-scheduler-policies"></a>Procedimiento Crear a agentes que usen directivas de programador específicas

Un agente es un componente de aplicación que funciona de forma asincrónica con otros componentes para resolver tareas de computación mayores. Normalmente, un agente tiene un ciclo de vida establecido y mantiene el estado.

Cada agente puede tener requisitos de aplicación únicos. Por ejemplo, un agente que permite la interacción con el usuario (ya sea al recuperar la entrada o al mostrar la salida) puede requerir un acceso más prioritario a los recursos informáticos. Las directivas de Scheduler permiten controlar la estrategia que el programador utiliza cuando administra tareas. En este tema se muestra cómo crear agentes que usen directivas de programador específicas.

Para obtener un ejemplo básico que usa directivas de programador personalizadas junto con bloques de mensajes asincrónicos, vea [Cómo: Especificar directivas de programador específicas](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md).

En este tema se usa la funcionalidad de la Biblioteca de agentes asincrónicos, como agentes, bloques de mensaje y funciones para pasar mensajes, para realizar el trabajo. Para obtener más información acerca de la biblioteca de agentes asincrónicos, vea [biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md).

## <a name="example"></a>Ejemplo

El siguiente ejemplo define dos clases que derivan de [Concurrency:: Agent](../../parallel/concrt/reference/agent-class.md): `permutor` y `printer`. La clase `permutor` calcula todas las permutaciones de una cadena de entrada determinada. La clase `printer` imprime los mensajes de progreso en la consola. La clase `permutor` realiza una operación que requiere gran cantidad de recursos de computación y que podría usar todos los recursos disponibles. Para ser útil, la clase `printer` debe imprimir cada mensaje de progreso de una manera puntual.

Para proporcionar la `printer` clase un acceso adecuado a los recursos informáticos, este ejemplo usa los pasos que se describen en [Cómo: Administrar una instancia del programador](../../parallel/concrt/how-to-manage-a-scheduler-instance.md) para crear una instancia del programador que tiene una directiva personalizada. La directiva personalizada especifica la prioridad del subproceso como la clase de prioridad máxima.

Para mostrar las ventajas de utilizar un programador que tiene una directiva personalizada, en el ejemplo se realiza la tarea dos veces. Primero se usa el programador predeterminado para programar ambas tareas. A continuación, se usa el programador predeterminado para programar el objeto `permutor` y un programador con una directiva personalizada para programar el objeto `printer`.

[!code-cpp[concrt-permute-strings#1](../../parallel/concrt/codesnippet/cpp/how-to-create-agents-that-use-specific-scheduler-policies_1.cpp)]

Este ejemplo produce el siguiente resultado:

```Output
With default scheduler:
Computing all permutations of 'Grapefruit'...
100% complete...

With higher context priority:
Computing all permutations of 'Grapefruit'...
100% complete...
```

Aunque ambos conjuntos de tareas generan el mismo resultado, la versión que usa la directiva personalizada permite que el objeto `printer` se ejecute con una prioridad elevada y, por tanto, con una mayor capacidad de respuesta.

## <a name="compiling-the-code"></a>Compilar el código

Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `permute-strings.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

**cl.exe/EHsc permute-strings.cpp**

## <a name="see-also"></a>Vea también

[Directivas de Scheduler](../../parallel/concrt/scheduler-policies.md)<br/>
[Agentes asincrónicos](../../parallel/concrt/asynchronous-agents.md)
