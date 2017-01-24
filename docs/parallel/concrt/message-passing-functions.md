---
title: "Funciones que pasan mensajes | Microsoft Docs"
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
  - "funciones que pasan mensajes"
ms.assetid: 42477c9e-a8a6-4dc4-a98e-93c6dc8c4dd0
caps.latest.revision: 23
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Funciones que pasan mensajes
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La Biblioteca de agentes asincrónicos proporciona varias funciones que permiten pasar mensajes entre los componentes.  
  
 Estas funciones para pasar mensajes se usan con los distintos tipos de bloques de mensajes.  Para obtener más información sobre los tipos de bloques de mensajes definidos por el Runtime de simultaneidad, vea [Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md).  
  
##  <a name="top"></a> Secciones  
 En este tema se describen las siguientes funciones para pasar mensajes:  
  
-   [send y asend](#send)  
  
-   [receive y try\_receive](#receive)  
  
-   [Ejemplos](#examples)  
  
##  <a name="send"></a> send y asend  
 La función de [concurrency::send](../Topic/send%20Function.md) envía un mensaje al destino especificado sincrónicamente y la función de [concurrency::asend](../Topic/asend%20Function.md) envía un mensaje al destino especificado de forma asincrónica.  Las funciones `send` y `asend` esperan hasta que el destino indica que aceptará o rechazará finalmente el mensaje.  
  
 La función `send` espera a que el destino acepte o rechace el mensaje antes de regresar.  La función `send` devuelve `true` si se entrega el mensaje; en caso contrario, devuelve `false`.  Dado que la función `send` funciona de manera sincrónica, la función `send` espera a que el destino reciba el mensaje antes de regresar.  
  
 Por el contrario, la función `asend` no espera a que el destino acepte o rechace el mensaje antes de regresar.  En su lugar, la función `asend` devuelve `true` si el destino acepta el mensaje y lo toma en última instancia.  De lo contrario, `asend` devuelve `false` para indicar que el destino rechazó el mensaje o pospuso la decisión de tomarlo.  
  
 \[[Arriba](#top)\]  
  
##  <a name="receive"></a> receive y try\_receive  
 [concurrency::receive](../Topic/receive%20Function.md) y [concurrency::try\_receive](../Topic/try_receive%20Function.md) funciona leer los datos de un origen determinado.  La función `receive` espera a que los datos estén disponibles, mientras que la función `try_receive` regresa inmediatamente.  
  
 Use la función `receive` cuando deba tener los datos para continuar.  Use la función `try_receive` si no debe bloquear el contexto actual o no tiene que tener los datos para continuar.  
  
 \[[Arriba](#top)\]  
  
##  <a name="examples"></a> Ejemplos  
 Para obtener ejemplos en los que se usan las funciones `send`, `asend` y `receive`, vea los temas siguientes:  
  
-   [Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)  
  
-   [Cómo: Implementar varios modelos productor\-consumidor](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)  
  
-   [Cómo: Proporcionar funciones de trabajo a las clases call y transformer](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)  
  
-   [Cómo: Usar la clase transformer en una canalización de datos](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)  
  
-   [Cómo: Seleccionar tareas completadas](../../parallel/concrt/how-to-select-among-completed-tasks.md)  
  
-   [Cómo: Enviar un mensaje a intervalos periódicos](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)  
  
-   [Cómo: Utilizar un filtro de bloque de mensaje](../../parallel/concrt/how-to-use-a-message-block-filter.md)  
  
 \[[Arriba](#top)\]  
  
## Vea también  
 [Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md)   
 [Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)   
 [send \(Función\)](../Topic/send%20Function.md)   
 [asend \(Función\)](../Topic/asend%20Function.md)   
 [receive \(Función\)](../Topic/receive%20Function.md)   
 [try\_receive \(Función\)](../Topic/try_receive%20Function.md)