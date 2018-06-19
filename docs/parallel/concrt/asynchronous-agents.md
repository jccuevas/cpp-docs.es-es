---
title: Agentes asincrónicos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- asynchronous agents
- agents [Concurrency Runtime]
ms.assetid: 6cf6ccc6-87f1-4e14-af15-ea8ba58fef1a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8649ebe0451e4352b27989563a1a0918afcb5a01
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33687984"
---
# <a name="asynchronous-agents"></a>Agentes asincrónicos
Un *agente asincrónico* (o simplemente *agente*) es un componente de aplicación que funciona de forma asincrónica con otros agentes para resolver tareas de computación mayores. Considere un agente como una tarea que tiene un ciclo de vida establecido. Por ejemplo, un agente podría leer datos de un dispositivo de entrada/salida (por ejemplo, el teclado, un archivo de disco o una conexión de red) y otro agente podrían realizar una acción en los datos cuando se encuentre disponible. El primer agente utiliza el paso de mensajes para informar al segundo de que hay más datos disponibles. El programador de tareas del Runtime de simultaneidad proporciona un mecanismo eficaz para permiten a los agentes bloquear y producir de forma cooperativa sin necesidad de adelantamiento menos eficiente.  
  

 La biblioteca de agentes define la [Concurrency](../../parallel/concrt/reference/agent-class.md) clase para representar un agente asincrónico. `agent` es una clase abstracta que declara el método virtual [concurrency::agent::run](reference/agent-class.md#run). El `run` método ejecuta la tarea que realiza el agente. Dado que `run` es abstracta, debe implementar este método en todas las clases que derivan de `agent`.  
  
## <a name="agent-life-cycle"></a>Ciclo de vida de agente  
 Los agentes tienen un ciclo de vida establecido. El [concurrency::agent_status](reference/concurrency-namespace-enums.md#agent_status) enumeración define los diversos estados de un agente. En la siguiente ilustración es un diagrama de estado que muestra el progresan de los agentes de un estado a otro. En esta ilustración, las líneas sólidas representan los métodos que se llama desde la aplicación; líneas de puntos representan los métodos que se llaman desde el tiempo de ejecución.  
  
 ![Diagrama de estado del agente](../../parallel/concrt/media/agentstate.png "agentstate")  
  
 La tabla siguiente describe cada estado de la `agent_status` enumeración.  
  
|Estado del agente|Descripción|  
|-----------------|-----------------|  
|`agent_created`|No se ha programado el agente para su ejecución.|  
|`agent_runnable`|El runtime programa al agente para su ejecución.|  
|`agent_started`|El agente se ha iniciado y se está ejecutando.|  
|`agent_done`|El agente finalizó.|  
|`agent_canceled`|El agente se canceló antes de que especifique la `started` estado.|  
  
 `agent_created` es el estado inicial de un agente, `agent_runnable` y `agent_started` son los estados activos, y `agent_done` y `agent_canceled` son los Estados de terminal.  
  
 Use la [concurrency::agent::status](reference/agent-class.md#status) método para recuperar el estado actual de un `agent` objeto. Aunque la `status` método es seguro para simultaneidad, puede cambiar el estado del agente en el momento en el `status` devuelve del método. Por ejemplo, podría ser un agente en el `agent_started` estado cuando se llama a la `status` método, pero se movió a la `agent_done` estado justo después el `status` devuelve del método.  

  
## <a name="methods-and-features"></a>Métodos y características  
 La tabla siguiente muestran algunos de los métodos importantes que pertenecen a la `agent` clase. Para obtener más información acerca de todos los `agent` métodos de la clase, vea [agent (clase)](../../parallel/concrt/reference/agent-class.md).  
  
|Método|Descripción|  
|------------|-----------------|  
|[start](reference/agent-class.md#start)|Programaciones la `agent` objeto para su ejecución y lo establece en el `agent_runnable` estado.|  
|[run](reference/agent-class.md#run)|Ejecuta la tarea que se debe realizar la `agent` objeto.|  
|[Realiza](reference/agent-class.md#done)|Mueve un agente para el `agent_done` estado.|  
|[Cancelar](../../parallel/concrt/cancellation-in-the-ppl.md#cancel)|Si no se inició el agente, este método cancela la ejecución del agente y lo establece en el `agent_canceled` estado.|  
|[status](reference/agent-class.md#status)|Recupera el estado actual de la `agent` objeto.|  
|[espera](reference/agent-class.md#wait)|Espera a que el `agent` objeto que se va a escribir el `agent_done` o `agent_canceled` estado.|  
|[wait_for_all](reference/agent-class.md#wait_for_all)|Espera a que todas ellas cuentan `agent` objetos que se va a escribir el `agent_done` o `agent_canceled` estado.|  
|[wait_for_one](reference/agent-class.md#wait_for_one)|Espera a que al menos uno de los proporcionados `agent` objetos que se va a escribir el `agent_done` o `agent_canceled` estado.|  
  
 Después de crear un objeto de agente, llame a la [Concurrency](reference/agent-class.md#start) método para programar su ejecución. El runtime llama el `run` método después de que se programa el agente y se establece en el `agent_runnable` estado.  
  
 El runtime no administra las excepciones producidas por agentes asincrónicos. Para obtener más información sobre el control de excepciones y los agentes, consulte [Exception Handling](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).  
  
## <a name="example"></a>Ejemplo  
 Para obtener un ejemplo que muestra cómo crear una aplicación basada en agente básica, vea [Tutorial: crear una aplicación basada en agente](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md).  
  
## <a name="see-also"></a>Vea también  
 [Biblioteca de agentes asincrónicos](../../parallel/concrt/asynchronous-agents-library.md)

