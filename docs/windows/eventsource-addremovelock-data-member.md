---
title: "EventSource::addRemoveLock_ (Miembro de datos) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "event/Microsoft::WRL::EventSource::addRemoveLock_"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "addRemoveLock_ (miembro de datos)"
ms.assetid: e2d69256-4891-4aad-ad0b-76479c0bb076
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# EventSource::addRemoveLock_ (Miembro de datos)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Sincroniza el acceso a la [targets_](../Topic/EventSource::targets_%20Data%20Member.md) matriz al agregar, quitar o invocar controladores de eventos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Wrappers::SRWLock addRemoveLock_;  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** event.h  
  
 **Espacio de nombres:** Microsoft::WRL
 
 ## <a name="see-also"></a>Vea también
 [EventSource (clase)](../windows/eventsource-class.md)