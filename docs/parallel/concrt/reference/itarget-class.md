---
title: "ITarget (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::ITarget"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ITarget (clase)"
ms.assetid: 5678db25-112a-4f72-be13-42e16b67c48b
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# ITarget (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

La clase `ITarget` es la interfaz para todos los bloques de destino.  Los bloques de destinos consumen mensajes ofrecidos por los bloques `ISource`.  
  
## Sintaxis  
  
```  
template<  
   class _Type  
>  
class ITarget;  
```  
  
#### Parámetros  
 `_Type`  
 El tipo de datos de la carga dentro de los mensajes aceptados por este bloque de destino.  
  
## Miembros  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`filter_method`|La firma de cualquier método que usa el bloque que devuelve un valor `bool` para determinar si se debería aceptar un mensaje proporcionado.|  
|`type`|Un alias de tipo para `_Type`.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ITarget::~ITarget \(Destructor\)](../Topic/ITarget::~ITarget%20Destructor.md)|Destruye el objeto `ITarget`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ITarget::propagate \(Método\)](../Topic/ITarget::propagate%20Method.md)|Cuando se invalida en una clase derivada, de forma asincrónica pasa un mensaje de un bloque de origen a este bloque de destino.|  
|[ITarget::send \(Método\)](../Topic/ITarget::send%20Method.md)|Cuando se invalida en una clase derivada, de forma sincrónica pasa un mensaje al bloque de destino.|  
|[ITarget::supports\_anonymous\_source \(Método\)](../Topic/ITarget::supports_anonymous_source%20Method.md)|Cuando se reemplaza en una clase derivada, devuelve true o false dependiendo de si el bloque de mensajes acepta los mensajes proporcionados por un origen que no se vincula al.  Si el método reemplazado devuelve `true`, el destino no puede posponer un mensaje proporcionado, como el consumo de un mensaje pospuesto posteriormente requiere el origen identificar en el registro de vínculo de sourse.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ITarget::link\_source \(Método\)](../Topic/ITarget::link_source%20Method.md)|Cuando se invalida en una clase derivada, vincula un bloque de origen especificado a este bloque `ITarget`.|  
|[ITarget::unlink\_source \(Método\)](../Topic/ITarget::unlink_source%20Method.md)|Cuando se invalida en una clase derivada, desvincula un bloque de origen especificado de este bloque `ITarget`.|  
|[ITarget::unlink\_sources \(Método\)](../Topic/ITarget::unlink_sources%20Method.md)|Cuando se invalida en una clase derivada, desvincula todos los bloques de origen de este bloque `ITarget`.|  
  
## Comentarios  
 Para obtener más información, vea [Bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## Jerarquía de herencia  
 `ITarget`  
  
## Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [ISource \(Clase\)](../../../parallel/concrt/reference/isource-class.md)