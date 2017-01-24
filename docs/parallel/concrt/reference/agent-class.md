---
title: "agent (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::agent"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "agent (clase)"
ms.assetid: 1b09e3d2-5e37-4966-b016-907ef1512456
caps.latest.revision: 20
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# agent (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Una clase diseñada para usarse como una clase base para todos los agentes independientes.  Se usa para ocultar el estado de otros agentes e interactuar con el paso de mensajes.  
  
## Sintaxis  
  
```  
class agent;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[agent::agent \(Constructor\)](../Topic/agent::agent%20Constructor.md)|Sobrecargado.  Construye un agente.|  
|[agent::~agent \(Destructor\)](../Topic/agent::~agent%20Destructor.md)|Destruye el agente.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[agent::cancel \(Método\)](../Topic/agent::cancel%20Method.md)|Mueve un agente de los estados `agent_created` o `agent_runnable` al estado `agent_canceled`.|  
|[agent::start \(Método\)](../Topic/agent::start%20Method.md)|Mueve un agente del estado `agent_created` al estado `agent_runnable` y lo programa para ejecución.|  
|[agent::status \(Método\)](../Topic/agent::status%20Method.md)|Un origen sincrónico de información del estado del agente.|  
|[agent::status\_port \(Método\)](../Topic/agent::status_port%20Method.md)|Un origen asincrónico de información del estado del agente.|  
|[agent::wait \(Método\)](../Topic/agent::wait%20Method.md)|Espera que un agente complete su tarea.|  
|[agent::wait\_for\_all \(Método\)](../Topic/agent::wait_for_all%20Method.md)|Espera que todos los agentes especificados completen sus tareas.|  
|[agent::wait\_for\_one \(Método\)](../Topic/agent::wait_for_one%20Method.md)|Espera que cualquiera de los agentes especificados complete sus tareas.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[agent::done \(Método\)](../Topic/agent::done%20Method.md)|Mueve un agente al estado `agent_done`, indicando que el agente se ha completado.|  
|[agent::run \(Método\)](../Topic/agent::run%20Method.md)|Representa la tarea principal de un agente.  `run` se deben invalidar en una clase derivada y especificar lo que el agente debería hacer una vez iniciado.|  
  
## Comentarios  
 Para obtener más información, vea [Agentes asincrónicos](../../../parallel/concrt/asynchronous-agents.md).  
  
## Jerarquía de herencia  
 `agent`  
  
## Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)