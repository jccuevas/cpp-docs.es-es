---
title: 'Cómo: Enviar un mensaje a intervalos periódicos'
ms.date: 11/04/2016
helpviewer_keywords:
- timer class, example
- sending messages at regular intervals [Concurrency Runtime]
ms.assetid: 4b60ea6c-97c8-4d69-9f7b-ad79f3548026
ms.openlocfilehash: 05777b0c00f587f588a50733d5113d9a7362d247
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549622"
---
# <a name="how-to-send-a-message-at-a-regular-interval"></a>Cómo: Enviar un mensaje a intervalos periódicos

En este ejemplo se muestra cómo usar la simultaneidad::[clase timer](../../parallel/concrt/reference/timer-class.md) para enviar un mensaje a intervalos regulares.

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se usa un objeto `timer` para notificar el progreso de una operación larga. Este ejemplo vincula el `timer` objeto a un [Concurrency:: call](../../parallel/concrt/reference/call-class.md) objeto. El objeto `call` imprime un indicador de progreso en la consola a intervalos periódicos. El [concurrency::timer::start](reference/timer-class.md#start) método ejecuta el temporizador en un contexto independiente. El `perform_lengthy_operation` llamadas de función el [Concurrency:: wait](reference/concurrency-namespace-functions.md#wait) función en el contexto principal para simular una operación lenta.

[!code-cpp[concrt-report-progress#1](../../parallel/concrt/codesnippet/cpp/how-to-send-a-message-at-a-regular-interval_1.cpp)]

Este ejemplo genera la siguiente salida de ejemplo:

```Output
Performing a lengthy operation..........done.
```

## <a name="compiling-the-code"></a>Compilar el código

Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `report-progress.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

**cl.exe/EHsc report-progress.cpp**

## <a name="see-also"></a>Vea también

[Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funciones que pasan mensajes](../../parallel/concrt/message-passing-functions.md)
