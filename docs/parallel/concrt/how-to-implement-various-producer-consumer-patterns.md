---
title: 'Cómo: Implementar varios modelos productor-consumidor'
ms.date: 11/04/2016
helpviewer_keywords:
- producer-consumer patterns, implementing [Concurrency Runtime]
- implementing producer-consumer patterns [Concurrency Runtime]
ms.assetid: 75f2c7cc-5399-49ea-98eb-847fe6747169
ms.openlocfilehash: 1c543e2c80ff9edea417fe8c1254bf9aa5aa37fd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658294"
---
# <a name="how-to-implement-various-producer-consumer-patterns"></a>Cómo: Implementar varios modelos productor-consumidor

En este tema se describe cómo implementar el modelo productor-consumidor en la aplicación. En este modelo, el *productor* envía mensajes a un bloque de mensajes y el *consumidor* lee los mensajes de este bloque.

En el tema se muestran dos escenarios. En el primero, el consumidor debe recibir cada mensaje que el productor envía. En el segundo, el consumidor busca datos periódicamente y, por tanto, no tiene que recibir cada mensaje.

Ambos ejemplos de este tema usan agentes, bloques de mensajes y funciones de paso de mensajes para transmitir mensajes del productor al consumidor. El agente del productor usa la [Concurrency:: Send](reference/concurrency-namespace-functions.md#send) función para escribir mensajes en un [Concurrency:: ITarget](../../parallel/concrt/reference/itarget-class.md) objeto. El agente del consumidor usa la [Concurrency:: Receive](reference/concurrency-namespace-functions.md#receive) función para leer mensajes desde un [Concurrency:: ISource](../../parallel/concrt/reference/isource-class.md) objeto. Ambos agentes almacenan un valor centinela para coordinar el final del procesamiento.

Para obtener más información sobre los agentes asincrónicos, vea [agentes asincrónicos](../../parallel/concrt/asynchronous-agents.md). Para obtener más información sobre los bloques de mensajes y las funciones de paso de mensajes, vea [bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md) y [Message Passing Functions](../../parallel/concrt/message-passing-functions.md).

## <a name="example"></a>Ejemplo

En este ejemplo, el agente del productor envía una serie de números al agente del consumidor. El consumidor recibe cada uno de estos números y calcula su promedio. La aplicación escribe el promedio en la consola.

Este ejemplo se usa un [Concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) objeto para permitir al productor en cola los mensajes. La clase `unbounded_buffer` implementa `ITarget` e `ISource` para que el productor y el consumidor puedan enviar y recibir mensajes en un búfer compartido. Las funciones `send` y `receive` coordinan la tarea de propagación de los datos del productor al consumidor.

[!code-cpp[concrt-producer-consumer-average#1](../../parallel/concrt/codesnippet/cpp/how-to-implement-various-producer-consumer-patterns_1.cpp)]

Este ejemplo produce el siguiente resultado:

```Output
The average is 50.
```

## <a name="example"></a>Ejemplo

En este ejemplo, el agente del productor envía una serie de cotizaciones al agente del consumidor. El agente del consumidor lee periódicamente la cotización actual y la imprime en la consola.

En este ejemplo se parece el anterior, salvo que usa un [Concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) objeto para permitir al productor compartir un mensaje con el consumidor. Como en el ejemplo anterior, la clase `overwrite_buffer` implementa `ITarget` e `ISource` para que el productor y el consumidor puedan actuar en un búfer de mensajes compartido.

[!code-cpp[concrt-producer-consumer-quotes#1](../../parallel/concrt/codesnippet/cpp/how-to-implement-various-producer-consumer-patterns_2.cpp)]

Este ejemplo genera la siguiente salida de ejemplo.

```Output
Current quote is 24.44.
Current quote is 24.44.
Current quote is 24.65.
Current quote is 24.99.
Current quote is 23.76.
Current quote is 22.30.
Current quote is 25.89.
```

A diferencia de lo que sucede con un objeto `unbounded_buffer`, la función `receive` no quita el mensaje del objeto `overwrite_buffer`. Si el consumidor lee del búfer de mensajes más de una vez antes de que el productor sobrescriba dicho mensaje, el receptor obtiene el mismo mensaje cada vez.

## <a name="compiling-the-code"></a>Compilar el código

Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `producer-consumer.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

**cl.exe/EHsc producer-consumer.cpp**

## <a name="see-also"></a>Vea también

[Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Agentes asincrónicos](../../parallel/concrt/asynchronous-agents.md)<br/>
[Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funciones que pasan mensajes](../../parallel/concrt/message-passing-functions.md)
