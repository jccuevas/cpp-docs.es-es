---
title: Funciones que pasan mensajes | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: message passing functions
ms.assetid: 42477c9e-a8a6-4dc4-a98e-93c6dc8c4dd0
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f9c2daa3f34ba4e73b28e11241d0f64680851fcc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="message-passing-functions"></a>Funciones que pasan mensajes
La biblioteca de agentes asincrónicos proporciona varias funciones que le permiten pasar mensajes entre los componentes.  
  
 Estas funciones de paso de mensajes se utilizan con los distintos tipos de bloques de mensajes. Para obtener más información acerca de los tipos de bloques de mensajes definidos por el Runtime de simultaneidad, vea [los bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md).  
  
##  <a name="top"></a> Secciones  
 En este tema se describe las funciones de paso de mensajes siguientes:  
  
-   [Send y asend](#send)  
  
-   [recepción y try_receive](#receive)  
  
-   [Ejemplos](#examples)  
  
##  <a name="send"></a>Send y asend  

 El [Concurrency:: Send](reference/concurrency-namespace-functions.md#send) función envía un mensaje en el destino especificado de forma sincrónica y la [Concurrency:: asend](reference/concurrency-namespace-functions.md#asend) función envía un mensaje en el destino especificado de forma asincrónica. Tanto el `send` y `asend` funciones esperan hasta que el destino indica que puede aceptar o rechazar el mensaje.  
  
 El `send` función espera hasta que el destino acepte o rechace el mensaje antes de regresar. El `send` función devuelve `true` si el mensaje se entregó y `false` en caso contrario. Dado que la `send` función funciona de forma sincrónica, el `send` función espera a que el destino recibir el mensaje antes de regresar.  
  
 Por el contrario, el `asend` función no esperar a que el destino acepte o rechace el mensaje antes de regresar. En su lugar, el `asend` función devuelve `true` si el destino acepta el mensaje y finalmente la tendrá. En caso contrario, `asend` devuelve `false` para indicar que el destino rechazó el mensaje o pospone la decisión sobre si desea desconectar el mensaje.  
  
 [[Arriba](#top)]  
  
##  <a name="receive"></a>recepción y try_receive  

 El [Concurrency:: Receive](reference/concurrency-namespace-functions.md#receive) y [Concurrency:: try_receive](reference/concurrency-namespace-functions.md#try_receive) funciones leen datos de un origen determinado. El `receive` función espera los datos hasta que esté disponible, mientras que la `try_receive` función devuelve inmediatamente.  
  
 Use la `receive` funcionar cuando debe tener los datos para continuar. Use la `try_receive` funcionar si no debe bloquear el contexto actual o no tiene los datos necesarios para continuar.  
  
 [[Arriba](#top)]  
  
##  <a name="examples"></a> Ejemplos  
 Para obtener ejemplos que utilizan el `send` y `asend`, y `receive` funciones, vea los temas siguientes:  
  
-   [Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)  
  
-   [Procedimiento para implementar varios modelos productor-consumidor](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)  
  
-   [Procedimiento para proporcionar funciones de trabajo a las clases call y transformer](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)  
  
-   [Procedimiento para usar la clase transformer en una canalización de datos](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)  
  
-   [Procedimiento para seleccionar tareas completadas](../../parallel/concrt/how-to-select-among-completed-tasks.md)  
  
-   [Procedimiento para enviar un mensaje a intervalos periódicos](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)  
  
-   [Procedimiento para usar un filtro de bloque de mensaje](../../parallel/concrt/how-to-use-a-message-block-filter.md)  
  
 [[Arriba](#top)]  
  
## <a name="see-also"></a>Vea también  
 [Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md)   
 [Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Send (función)](reference/concurrency-namespace-functions.md#send)   
 [asend (función)](reference/concurrency-namespace-functions.md#asend)   
 [Receive (función)](reference/concurrency-namespace-functions.md#receive)   
 [try_receive (función)](reference/concurrency-namespace-functions.md#try_receive)


