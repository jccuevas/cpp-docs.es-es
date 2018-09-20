---
title: Funciones que pasan mensajes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message passing functions
ms.assetid: 42477c9e-a8a6-4dc4-a98e-93c6dc8c4dd0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b0b7a7afb25d46fa3b521353c4577fbed66e69fd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436993"
---
# <a name="message-passing-functions"></a>Funciones que pasan mensajes

La biblioteca de agentes asincrónicos proporciona varias funciones que le permiten pasar mensajes entre los componentes.

Estas funciones de paso de mensajes se utilizan con los distintos tipos de bloques de mensajes. Para obtener más información acerca de los tipos de bloques de mensajes definidos por el Runtime de simultaneidad, consulte [bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md).

##  <a name="top"></a> Secciones

En este tema se describe las funciones de paso de mensajes siguientes:

- [envío y asend](#send)

- [recepción y try_receive](#receive)

- [Ejemplos](#examples)

##  <a name="send"></a> envío y asend

El [Concurrency:: Send](reference/concurrency-namespace-functions.md#send) función envía un mensaje al destino especificado de forma sincrónica y la [Concurrency:: asend](reference/concurrency-namespace-functions.md#asend) función envía un mensaje al destino especificado de forma asincrónica. Tanto el `send` y `asend` funciones espere hasta que el destino indica que finalmente Aceptar o rechazar el mensaje.

El `send` función espera hasta que el destino acepta o rechaza el mensaje antes de devolver. El `send` función devuelve `true` si el mensaje se entregó y `false` en caso contrario. Dado que el `send` función funciona de forma sincrónica, el `send` función espera a que el destino recibir el mensaje antes de devolver.

Por el contrario, el `asend` función no espera a que el destino Aceptar o rechazar el mensaje antes de devolver. En su lugar, el `asend` función devuelve `true` si el destino acepta el mensaje y, finalmente, y realizará. En caso contrario, `asend` devuelve `false` para indicar que el destino rechazó el mensaje o pospone la decisión sobre si se debe tomar el mensaje.

[[Arriba](#top)]

##  <a name="receive"></a> recepción y try_receive

El [Concurrency:: Receive](reference/concurrency-namespace-functions.md#receive) y [Concurrency:: try_receive](reference/concurrency-namespace-functions.md#try_receive) funciones leen datos desde un origen determinado. El `receive` función espera los datos estén disponibles, mientras que el `try_receive` función devuelve inmediatamente.

Use el `receive` funcionar cuando debe tener los datos para continuar. Use el `try_receive` funcionar si no debe bloquear el contexto actual o no es necesario para que los datos para continuar.

[[Arriba](#top)]

##  <a name="examples"></a> Ejemplos

Para obtener ejemplos que utilizan el `send` y `asend`, y `receive` funciones, vea los temas siguientes:

- [Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)

- [Procedimiento para implementar varios modelos productor-consumidor](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)

- [Procedimiento para proporcionar funciones de trabajo a las clases call y transformer](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)

- [Procedimiento para usar la clase transformer en una canalización de datos](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)

- [Procedimiento para seleccionar tareas completadas](../../parallel/concrt/how-to-select-among-completed-tasks.md)

- [Procedimiento para enviar un mensaje a intervalos periódicos](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)

- [Procedimiento para usar un filtro de bloque de mensaje](../../parallel/concrt/how-to-use-a-message-block-filter.md)

[[Arriba](#top)]

## <a name="see-also"></a>Vea también

[Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Send (función)](reference/concurrency-namespace-functions.md#send)<br/>
[asend (función)](reference/concurrency-namespace-functions.md#asend)<br/>
[Receive (función)](reference/concurrency-namespace-functions.md#receive)<br/>
[try_receive (función)](reference/concurrency-namespace-functions.md#try_receive)

