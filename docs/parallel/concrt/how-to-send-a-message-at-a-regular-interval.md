---
title: 'Cómo: Enviar un mensaje a intervalos periódicos'
ms.date: 11/04/2016
helpviewer_keywords:
- timer class, example
- sending messages at regular intervals [Concurrency Runtime]
ms.assetid: 4b60ea6c-97c8-4d69-9f7b-ad79f3548026
ms.openlocfilehash: c51a5cab6fcae5eb45b9d9b54c0dad8e8ec393b2
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142463"
---
# <a name="how-to-send-a-message-at-a-regular-interval"></a>Cómo: Enviar un mensaje a intervalos periódicos

En este ejemplo se muestra cómo usar la clase Concurrency::[Timer](../../parallel/concrt/reference/timer-class.md) para enviar un mensaje a intervalos regulares.

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se usa un objeto `timer` para notificar el progreso de una operación larga. En este ejemplo se vincula el objeto `timer` a un objeto [Concurrency:: Call](../../parallel/concrt/reference/call-class.md) . El objeto `call` imprime un indicador de progreso en la consola a intervalos periódicos. El método [Concurrency:: Timer:: Start](reference/timer-class.md#start) ejecuta el temporizador en un contexto independiente. La función `perform_lengthy_operation` llama a la función [Concurrency:: wait](reference/concurrency-namespace-functions.md#wait) en el contexto principal para simular una operación que requiere mucho tiempo.

[!code-cpp[concrt-report-progress#1](../../parallel/concrt/codesnippet/cpp/how-to-send-a-message-at-a-regular-interval_1.cpp)]

Este ejemplo genera la siguiente salida de ejemplo:

```Output
Performing a lengthy operation..........done.
```

## <a name="compiling-the-code"></a>Compilar el código

Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `report-progress.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.

> **cl. exe/EHsc Report-Progress. cpp**

## <a name="see-also"></a>Consulte también

[Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Funciones que pasan mensajes](../../parallel/concrt/message-passing-functions.md)
