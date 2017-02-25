---
title: "AsyncBase::GetOnProgress (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "async/Microsoft::WRL::AsyncBase::GetOnProgress"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetOnProgress (método)"
ms.assetid: 286ddc9c-3e30-41a2-8e8b-e53d3fb0649d
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# AsyncBase::GetOnProgress (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Copie la dirección del controlador de eventos actual de progreso en la variable especificada.  
  
## Sintaxis  
  
```  
STDMETHOD(  
   GetOnProgress  
)(TProgress** progressHandler);  
```  
  
#### Parámetros  
 `progressHandler`  
 La ubicación donde se almacena la dirección del controlador de eventos actual de progreso.  
  
## Valor devuelto  
 S\_OK si correctamente; si no, E\_ILLEGAL\_METHOD\_CALL.  
  
## Requisitos  
 **Encabezado:** async.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [AsyncBase \(Clase\)](../windows/asyncbase-class.md)