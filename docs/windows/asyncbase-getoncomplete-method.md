---
title: "AsyncBase::GetOnComplete (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "async/Microsoft::WRL::AsyncBase::GetOnComplete"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetOnComplete (método)"
ms.assetid: f06ae02d-9a88-41d2-b749-bdc1a7ff8748
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# AsyncBase::GetOnComplete (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Copie la dirección del controlador de eventos actual de finalización a la variable especificada.  
  
## Sintaxis  
  
```  
STDMETHOD(  
   GetOnComplete  
)(TComplete** completeHandler);  
```  
  
#### Parámetros  
 `completeHandler`  
 La ubicación donde se almacena la dirección del controlador de eventos actual de finalización.  
  
## Valor devuelto  
 S\_OK si correctamente; si no, E\_ILLEGAL\_METHOD\_CALL.  
  
## Requisitos  
 **Encabezado:** async.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [AsyncBase \(Clase\)](../windows/asyncbase-class.md)