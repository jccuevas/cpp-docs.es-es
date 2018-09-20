---
title: 'Cómo: enviar un mensaje a intervalos regulares | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- timer class, example
- sending messages at regular intervals [Concurrency Runtime]
ms.assetid: 4b60ea6c-97c8-4d69-9f7b-ad79f3548026
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b3c476d9cf633ce9b676dc8f658c94bd0b240461
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46384304"
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
