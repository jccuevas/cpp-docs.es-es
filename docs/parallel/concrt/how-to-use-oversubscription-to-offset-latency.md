---
title: 'Cómo: usar la suscripción excesiva para compensar la latencia | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- oversubscription, using [Concurrency Runtime]
- using oversubscription [Concurrency Runtime]
ms.assetid: a1011329-2f0a-4afb-b599-dd4043009a10
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0c27864d040d0b6ce7b36087cff85ed750aa7ed2
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-use-oversubscription-to-offset-latency"></a>Cómo: Usar la suscripción excesiva para compensar la latencia
La suscripción excesiva puede mejorar la eficacia general de algunas aplicaciones que contienen tareas con una latencia elevada. En este tema se muestra cómo utilizar la suscripción excesiva para compensar la latencia que se produce al leer datos de una conexión de red.  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo se utiliza la [biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md) para descargar archivos desde los servidores HTTP. El `http_reader` clase se deriva de [Concurrency](../../parallel/concrt/reference/agent-class.md) y utiliza el paso para leer de forma asincrónica qué nombres de URL de descarga de mensajes.  
  
 El `http_reader` clase utiliza el [Concurrency:: task_group](reference/task-group-class.md) clase para leer cada archivo simultáneamente. Cada tarea llama a la [concurrency::Context::Oversubscribe](reference/context-class.md#oversubscribe) método con el `_BeginOversubscription` parámetro establecido en `true` para habilitar la sobresuscripción en el contexto actual. Cada tarea, a continuación, utiliza Microsoft Foundation Classes (MFC) [CInternetSession](../../mfc/reference/cinternetsession-class.md) y [CHttpFile](../../mfc/reference/chttpfile-class.md) clases para descargar el archivo. Finalmente, cada tarea llama a `Context::Oversubscribe` con el parámetro `_BeginOversubscription` establecido en `false` para deshabilitar la suscripción excesiva.  
  
 Cuando la suscripción excesiva está habilitada, el runtime crea un subproceso adicional en el que ejecutar las tareas. Cada uno de estos subprocesos también puede suscribir en exceso el contexto actual y crear de este modo subprocesos adicionales. El `http_reader` clase utiliza un [Concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) objeto para limitar el número de subprocesos que utiliza la aplicación. El agente inicializa el búfer con un número fijo de valores de token. Para cada operación de descarga, el agente lee un valor de token del búfer antes de que se inicie la operación y, a continuación, escribe el valora de vuelta en el búfer cuando la operación finaliza. Cuando el búfer está vacío, el agente espera a que una de las operaciones de la descarga vuelva a escribir un valor en el búfer.  
  
 En el siguiente ejemplo se limita el número de tareas simultáneas a dos veces el número de subprocesos de hardware disponibles. Este valor es un buen punto de partida cuando se experimenta con la suscripción excesiva. Puede utilizar un valor que ajusta un entorno del procesamiento determinado o cambiar dinámicamente este valor para responder a la carga de trabajo.  
  
 [!code-cpp[concrt-download-oversubscription#1](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_1.cpp)]  
  
 En este ejemplo se genera el siguiente resultado en un equipo que tiene cuatro procesadores:  
  
```Output  
Downloading http://www.adatum.com/...  
Downloading http://www.adventure-works.com/...  
Downloading http://www.alpineskihouse.com/...  
Downloading http://www.cpandl.com/...  
Downloading http://www.cohovineyard.com/...  
Downloading http://www.cohowinery.com/...  
Downloading http://www.cohovineyardandwinery.com/...  
Downloading http://www.contoso.com/...  
Downloading http://www.consolidatedmessenger.com/...  
Downloading http://www.fabrikam.com/...  
Downloading http://www.fourthcoffee.com/...  
Downloading http://www.graphicdesigninstitute.com/...  
Downloading http://www.humongousinsurance.com/...  
Downloading http://www.litwareinc.com/...  
Downloading http://www.lucernepublishing.com/...  
Downloading http://www.margiestravel.com/...  
Downloading http://www.northwindtraders.com/...  
Downloading http://www.proseware.com/...  
Downloading http://www.fineartschool.net...  
Downloading http://www.tailspintoys.com/...  
Downloaded 1801040 bytes in 3276 ms.  
```  
  
 El ejemplo se puede ejecutar más rápidamente cuando la suscripción excesiva está habilitada porque las tareas adicionales se ejecutan mientras otras esperan hasta que una operación latente finalice.  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Copie el código de ejemplo y péguelo en un proyecto de Visual Studio o péguelo en un archivo denominado `download-oversubscription.cpp` y, a continuación, ejecute uno de los siguientes comandos en una ventana de símbolo del sistema de Visual Studio.  
  
 **cl.exe/EHsc /MD /D "_AFXDLL" download-oversubscription.cpp**  
  
 **cl.exe/EHsc /MT download-oversubscription.cpp**  
  
## <a name="robust-programming"></a>Programación sólida  
 Deshabilite siempre la suscripción excesiva una vez que no la necesite. Considere una función que no controla una excepción que produce otra función. Si no deshabilita la suscripción excesiva antes de que la función vuelva, cualquier trabajo paralelo adicional también suscribirá en exceso el contexto actual.  
  
 Puede usar el *Resource Acquisition Is Initialization* patrón (RAII) para limitar la suscripción excesiva a un ámbito determinado. Bajo el modelo RAII, se asigna una estructura de datos en la pila. Esa estructura de datos se inicializa o adquiere un recurso cuando se crea, y destruye o libera ese recurso cuando se destruye la estructura de datos. El modelo RAII garantiza que se llama al destructor antes de que el ámbito de inclusión salga. Por consiguiente, se administra el recurso correctamente cuando se produce una excepción o cuando una función contiene varias instrucciones `return`.  
  
 En el siguiente ejemplo se define una estructura que se denomina `scoped_blocking_signal`. El constructor de la estructura `scoped_blocking_signal` habilita la suscripción excesiva y el destructor la deshabilita.  
  
 [!code-cpp[concrt-download-oversubscription#2](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_2.cpp)]  
  
 En el siguiente ejemplo se modifica el cuerpo del método `download` para utilizar RAII y asegurar que la suscripción excesiva se deshabilite antes de que la función vuelva. Esta técnica asegura que el método `download` es seguro ante excepciones.  
  
 [!code-cpp[concrt-download-oversubscription#3](../../parallel/concrt/codesnippet/cpp/how-to-use-oversubscription-to-offset-latency_3.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Contextos](../../parallel/concrt/contexts.md)   
 [Context:: Oversubscribe (método)](reference/context-class.md#oversubscribe)


