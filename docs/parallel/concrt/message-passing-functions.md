---
title: Funciones que pasan mensajes
ms.date: 11/04/2016
helpviewer_keywords:
- message passing functions
ms.assetid: 42477c9e-a8a6-4dc4-a98e-93c6dc8c4dd0
ms.openlocfilehash: 4e1052a59f355c4ad5a7c6b57724268c24a209b4
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143300"
---
# <a name="message-passing-functions"></a>Funciones que pasan mensajes

La biblioteca de agentes asincrónicos proporciona varias funciones que permiten pasar mensajes entre componentes.

Estas funciones de paso de mensajes se usan con los distintos tipos de bloques de mensajes. Para obtener más información sobre los tipos de bloques de mensajes definidos por el Runtime de simultaneidad, consulte [bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="top"></a> Secciones

En este tema se describen las siguientes funciones de paso de mensajes:

- [Send y Asend](#send)

- [Receive y try_receive](#receive)

- [Ejemplos](#examples)

## <a name="send"></a>Send y Asend

La función [Concurrency:: Send](reference/concurrency-namespace-functions.md#send) envía un mensaje al destino especificado sincrónicamente y la función [Concurrency:: Asend](reference/concurrency-namespace-functions.md#asend) envía un mensaje al destino especificado de forma asincrónica. Las funciones `send` y `asend` esperan hasta que el destino indique que finalmente aceptará o rechazará el mensaje.

La función `send` espera hasta que el destino acepta o rechaza el mensaje antes de que se devuelva. La función `send` devuelve **true** si el mensaje se entregó y **false** en caso contrario. Dado que la función `send` funciona sincrónicamente, la función `send` espera a que el destino reciba el mensaje antes de que se devuelva.

Por el contrario, la función `asend` no espera a que el destino acepte o rechace el mensaje antes de que se devuelva. En su lugar, la función `asend` devuelve **true** si el destino acepta el mensaje y, finalmente, lo toma. De lo contrario, `asend` devuelve **false** para indicar que el destino rechazó el mensaje o pospuso la decisión sobre si se va a tomar el mensaje.

[[Arriba](#top)]

## <a name="receive"></a>Receive y try_receive

Las funciones [Concurrency:: Receive](reference/concurrency-namespace-functions.md#receive) y [Concurrency:: try_receive](reference/concurrency-namespace-functions.md#try_receive) leen los datos de un origen determinado. La función `receive` espera a que los datos estén disponibles, mientras que la función `try_receive` vuelve inmediatamente.

Utilice la función `receive` cuando deba tener los datos para continuar. Utilice la función `try_receive` si no debe bloquear el contexto actual o no es necesario que los datos continúen.

[[Arriba](#top)]

## <a name="examples"></a> Ejemplos

Para obtener ejemplos que usan las funciones `send` y `asend`y `receive`, vea los temas siguientes:

- [Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)

- [Procedimiento para implementar varios modelos productor-consumidor](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)

- [Procedimiento para proporcionar funciones de trabajo a las clases call y transformer](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)

- [Procedimiento para usar la clase transformer en una canalización de datos](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)

- [Procedimiento para seleccionar tareas completadas](../../parallel/concrt/how-to-select-among-completed-tasks.md)

- [Procedimiento para enviar un mensaje a intervalos periódicos](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)

- [Procedimiento para usar un filtro de bloque de mensaje](../../parallel/concrt/how-to-use-a-message-block-filter.md)

[[Arriba](#top)]

## <a name="see-also"></a>Consulte también

[Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Send (función)](reference/concurrency-namespace-functions.md#send)<br/>
[Asend (función)](reference/concurrency-namespace-functions.md#asend)<br/>
[Receive (función)](reference/concurrency-namespace-functions.md#receive)<br/>
[try_receive función)](reference/concurrency-namespace-functions.md#try_receive)
