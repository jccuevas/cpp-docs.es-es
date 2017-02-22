---
title: "AsyncStatusInternal (Enumeraci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "async/Microsoft::WRL::Details::AsyncStatusInternal"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AsyncStatusInternal (enumeración)"
ms.assetid: b783923f-3f1c-4487-9384-be572cbc62d7
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# AsyncStatusInternal (Enumeraci&#243;n)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
enum AsyncStatusInternal;  
```  
  
## Comentarios  
 Especifica una asignación entre enumeraciones internas para el estado de operaciones asincrónicas y la enumeración de **Windows::Foundation::AsyncStatus** .  
  
## Miembros  
 `_Created`  
 Equivalente a ::Windows::Foundation::AsyncStatus::Created  
  
 `_Started`  
 Equivalente a ::Windows::Foundation::AsyncStatus::Started  
  
 `_Completed`  
 Equivalente a ::Windows::Foundation::AsyncStatus::Completed  
  
 `_Cancelled`  
 Equivalente a ::Windows::Foundation::AsyncStatus::Cancelled  
  
 `_Error`  
 Equivalente a ::Windows::Foundation::AsyncStatus::Error  
  
## Requisitos  
 **Encabezado:** async.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)