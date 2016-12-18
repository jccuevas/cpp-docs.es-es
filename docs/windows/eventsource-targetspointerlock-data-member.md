---
title: "EventSource::targetsPointerLock_ (Miembro de datos) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "event/Microsoft::WRL::EventSource::targetsPointerLock_"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "targetsPointerLock_ (miembro de datos)"
ms.assetid: 8f08409f-5262-4be7-9cf1-2ed15f19684a
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# EventSource::targetsPointerLock_ (Miembro de datos)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Sincroniza el acceso a miembros de datos internos incluso mientras se agregan controladores de eventos para este origen de eventos, quitar o invocar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Wrappers::SRWLock targetsPointerLock_;  
```  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** event.h  
  
 **Espacio de nombres:** Microsoft::WRL
 
 ## <a name="see-also"></a>Vea también
 [EventSource (clase)](../windows/eventsource-class.md)