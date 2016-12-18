---
title: "C&#243;mo: Enviar un mensaje a intervalos peri&#243;dicos | Microsoft Docs"
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
  - "timer (clase), ejemplo"
  - "enviar mensajes a intervalos regulares [Runtime de simultaneidad]"
ms.assetid: 4b60ea6c-97c8-4d69-9f7b-ad79f3548026
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Enviar un mensaje a intervalos peri&#243;dicos
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este ejemplo muestra cómo utilizar la simultaneidad::[clase timer](../../parallel/concrt/reference/timer-class.md) para enviar un mensaje a intervalos regulares.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se usa un objeto `timer` para notificar el progreso de una operación larga. Este ejemplo vincula el `timer` de objeto para un [Concurrency:: call](../../parallel/concrt/reference/call-class.md) objeto. El objeto `call` imprime un indicador de progreso en la consola a intervalos periódicos. El [concurrency::timer::start](../Topic/timer::start%20Method.md) método ejecuta el temporizador en un contexto independiente. El `perform_lengthy_operation` llamadas a funciones del [Concurrency:: wait](../Topic/wait%20Function.md) en el contexto principal para simular una operación que consume mucho tiempo.  
  
 [!code-cpp[concrt-report-progress#1](../../parallel/concrt/codesnippet/CPP/how-to-send-a-message-at-a-regular-interval_1.cpp)]  
  
 Este ejemplo genera la siguiente salida de ejemplo:  
  
```Output  
Performing a lengthy operation..........done.  
```  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `report-progress.cpp` y, a continuación, ejecute el siguiente comando en una ventana del símbolo del sistema de Visual Studio.  
  
 **cl.exe/EHsc report-progress.cpp**  
  
## <a name="see-also"></a>Vea también  
 [Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md)   
 [Bloques de mensajes asincrónicos](../../parallel/concrt/asynchronous-message-blocks.md)   
 [Funciones que pasan mensajes](../../parallel/concrt/message-passing-functions.md)
