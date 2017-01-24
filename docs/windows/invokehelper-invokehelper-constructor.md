---
title: "InvokeHelper::InvokeHelper (Constructor) | Microsoft Docs"
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
  - "event/Microsoft::WRL::Details::InvokeHelper::InvokeHelper"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "InvokeHelper, constructor"
ms.assetid: 0223c574-abc3-4fc0-99e6-38626ba79243
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# InvokeHelper::InvokeHelper (Constructor)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
explicit InvokeHelper(  
   TCallback callback  
);  
```  
  
#### Parámetros  
 `callback`  
 Un controlador de eventos.  
  
## Comentarios  
 Inicializa una nueva instancia de la clase de InvokeHelper.  
  
 El parámetro de plantilla de `TCallback` especifica el tipo del controlador de eventos.  
  
## Requisitos  
 **Encabezado:** event.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [InvokeHelper \(Estructura\)](../windows/invokehelper-structure.md)   
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)