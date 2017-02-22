---
title: "ISource (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::ISource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ISource (clase)"
ms.assetid: c7b73463-42f6-4dcc-801a-81379b12d35a
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# ISource (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

La clase `ISource` es la interfaz para todos los bloques de origen.  Los bloques de origen propagan mensajes a los bloques `ITarget`.  
  
## Sintaxis  
  
```  
template<  
   class _Type  
>  
class ISource;  
```  
  
#### Parámetros  
 `_Type`  
 El tipo de datos de la carga dentro de los mensajes producidos por este bloque de origen.  
  
## Miembros  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`source_type`|Un alias de tipo para `_Type`.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ISource::~ISource \(Destructor\)](../Topic/ISource::~ISource%20Destructor.md)|Destruye el objeto `ISource`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ISource::accept \(Método\)](../Topic/ISource::accept%20Method.md)|Cuando se invalida en una clase derivada, acepta un mensaje proporcionado por este bloque `ISource`, transfiriendo la propiedad al llamador.|  
|[ISource::acquire\_ref \(Método\)](../Topic/ISource::acquire_ref%20Method.md)|Cuando se invalida en una clase derivada, adquiere un recuento de referencias en este bloque `ISource`, para evitar la eliminación.|  
|[ISource::consume \(Método\)](../Topic/ISource::consume%20Method.md)|Cuando se invalida en una clase derivada, consume un mensaje proporcionado anteriormente por este bloque de mensajería `ISource` y correctamente reservado por el destino, transfiriendo la propiedad al llamador.|  
|[ISource::link\_target \(Método\)](../Topic/ISource::link_target%20Method.md)|Cuando se invalida en una clase derivada, vincula un bloque de destino especificado a este bloque `ISource`.|  
|[ISource::release \(Método\)](../Topic/ISource::release%20Method.md)|Cuando se invalida en una clase derivada, libera una reserva de mensaje anterior correcta.|  
|[ISource::release\_ref \(Método\)](../Topic/ISource::release_ref%20Method.md)|Cuando se invalida en una clase derivada, libera un recuento de referencias en este bloque `ISource`.|  
|[ISource::reserve \(Método\)](../Topic/ISource::reserve%20Method.md)|Cuando se invalida en una clase derivada, reserva un mensaje ofrecido previamente por este bloque `ISource`.|  
|[ISource::unlink\_target \(Método\)](../Topic/ISource::unlink_target%20Method.md)|Cuando se invalida en una clase derivada, desvincula un bloque de destino de este bloque `ISource`, si se encuentra vinculado previamente.|  
|[ISource::unlink\_targets \(Método\)](../Topic/ISource::unlink_targets%20Method.md)|Cuando se invalida en una clase derivada, desvincula todos los bloques de destino de este bloque `ISource`.|  
  
## Comentarios  
 Para obtener más información, vea [Bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## Jerarquía de herencia  
 `ISource`  
  
## Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [ITarget \(Clase\)](../../../parallel/concrt/reference/itarget-class.md)