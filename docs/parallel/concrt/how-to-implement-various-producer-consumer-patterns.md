---
title: "C&#243;mo: Implementar varios modelos productor-consumidor | Microsoft Docs"
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
  - "implementación de patrones productor-consumidor [Runtime de simultaneidad]"
  - "implementar modelos productor-consumidor [Runtime de simultaneidad]"
ms.assetid: 75f2c7cc-5399-49ea-98eb-847fe6747169
caps.latest.revision: 17
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Implementar varios modelos productor-consumidor
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En este tema se describe cómo implementar el modelo productor\-consumidor en la aplicación.  En este modelo, el *productor* envía mensajes a un bloque de mensajes y el *consumidor* lee los mensajes de este bloque.  
  
 En el tema se muestran dos escenarios.  En el primero, el consumidor debe recibir cada mensaje que el productor envía.  En el segundo, el consumidor busca datos periódicamente y, por tanto, no tiene que recibir cada mensaje.  
  
 Ambos ejemplos de este tema usan agentes, bloques de mensajes y funciones de paso de mensajes para transmitir mensajes del productor al consumidor.  El agente del productor usa la función [concurrency::send](../Topic/send%20Function.md) para escribir mensajes en un objeto [concurrency::ITarget](../../parallel/concrt/reference/itarget-class.md).  El agente del consumidor usa la función [concurrency::receive](../Topic/receive%20Function.md) para leer mensajes de un objeto [concurrency::ISource](../../parallel/concrt/reference/isource-class.md).  Ambos agentes almacenan un valor centinela para coordinar el final del procesamiento.  
  
 Para obtener más información sobre los agentes asincrónicos, vea [Agentes asincrónicos](../../parallel/concrt/asynchronous-agents.md).  Para obtener más información sobre los bloques de mensajes y las funciones de paso de mensajes, vea [Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md) y [Funciones que pasan mensajes](../../parallel/concrt/message-passing-functions.md).  
  
## Ejemplo  
 En este ejemplo, el agente del productor envía una serie de números al agente del consumidor.  El consumidor recibe cada uno de estos números y calcula su promedio.  La aplicación escribe el promedio en la consola.  
  
 En este ejemplo se usa un objeto [concurrency::unbounded\_buffer](../Topic/unbounded_buffer%20Class.md) para permitir al productor poner en cola los mensajes.  La clase `unbounded_buffer` implementa `ITarget` e `ISource` para que el productor y el consumidor puedan enviar y recibir mensajes en un búfer compartido.  Las funciones `send` y `receive` coordinan la tarea de propagación de los datos del productor al consumidor.  
  
 [!code-cpp[concrt-producer-consumer-average#1](../../parallel/concrt/codesnippet/CPP/how-to-implement-various-producer-consumer-patterns_1.cpp)]  
  
 Este ejemplo produce el siguiente resultado:  
  
  **The average is 50.**   
## Ejemplo  
 En este ejemplo, el agente del productor envía una serie de cotizaciones al agente del consumidor.  El agente del consumidor lee periódicamente la cotización actual y la imprime en la consola.  
  
 Este ejemplo es similar al anterior, excepto por el hecho de que usa un objeto [concurrency::overwrite\_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) para permitir al productor compartir un mensaje con el consumidor.  Como en el ejemplo anterior, la clase `overwrite_buffer` implementa `ITarget` e `ISource` para que el productor y el consumidor puedan actuar en un búfer de mensajes compartido.  
  
 [!code-cpp[concrt-producer-consumer-quotes#1](../../parallel/concrt/codesnippet/CPP/how-to-implement-various-producer-consumer-patterns_2.cpp)]  
  
 Este ejemplo genera la siguiente salida de ejemplo.  
  
  **Current quote is 24.44.**  
**Current quote is 24.44.**  
**Current quote is 24.65.**  
**Current quote is 24.99.**  
**Current quote is 23.76.**  
**Current quote is 22.30.**  
**Current quote is 25.89.** A diferencia de lo que sucede con un objeto `unbounded_buffer`, la función `receive` no quita el mensaje del objeto `overwrite_buffer`.  Si el consumidor lee del búfer de mensajes más de una vez antes de que el productor sobrescriba dicho mensaje, el receptor obtiene el mismo mensaje cada vez.  
  
## Compilar el código  
 Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o en un archivo denominado `producer-consumer.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.  
  
 **cl.exe \/EHsc producer\-consumer.cpp**  
  
## Vea también  
 [Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md)   
 [Agentes asincrónicos](../../parallel/concrt/asynchronous-agents.md)   
 [Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Funciones que pasan mensajes](../../parallel/concrt/message-passing-functions.md)