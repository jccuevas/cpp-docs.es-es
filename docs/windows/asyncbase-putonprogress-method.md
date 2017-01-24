---
title: "AsyncBase::PutOnProgress (M&#233;todo) | Microsoft Docs"
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
  - "async/Microsoft::WRL::AsyncBase::PutOnProgress"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PutOnProgress (método)"
ms.assetid: 1f5f180e-eb5a-4afe-ac16-69dbf36f0383
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AsyncBase::PutOnProgress (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Establece la dirección del controlador de eventos de progreso al valor especificado.  
  
## Sintaxis  
  
```  
STDMETHOD(  
   PutOnProgress  
)(TProgress* progressHandler);  
```  
  
#### Parámetros  
 `progressHandler`  
 La dirección que establecen el controlador de eventos de progreso.  
  
## Valor devuelto  
 S\_OK si correctamente; si no, E\_ILLEGAL\_METHOD\_CALL.  
  
## Requisitos  
 **Encabezado:** async.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [AsyncBase \(Clase\)](../windows/asyncbase-class.md)