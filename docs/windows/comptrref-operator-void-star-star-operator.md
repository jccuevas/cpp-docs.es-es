---
title: "ComPtrRef::operator void** (Operador) | Microsoft Docs"
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
  - "client/Microsoft::WRL::Details::ComPtrRef::operator void**"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator void** (operador)"
ms.assetid: f020045c-9de4-4392-8783-73f0fc0761c6
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtrRef::operator void** (Operador)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
operator void**() const;  
```  
  
## Comentarios  
 Elimina el objeto actual de ComPtrRef, convierte el puntero a la interfaz que se representada por el objeto de ComPtrRef como a puntero\-a\-puntero\- a `void`, y devuelve el puntero de la conversión.  
  
## Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [ComPtrRef \(Clase\)](../Topic/ComPtrRef%20Class.md)   
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)