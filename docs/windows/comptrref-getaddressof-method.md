---
title: "ComPtrRef::GetAddressOf (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "client/Microsoft::WRL::Details::ComPtrRef::GetAddressOf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetAddressOf (método)"
ms.assetid: 797df323-a2fa-412b-ab60-32cce3721096
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# ComPtrRef::GetAddressOf (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
InterfaceType* const * GetAddressOf() const;  
```  
  
## Valor devuelto  
 Dirección de un puntero a la interfaz representada por el objeto actual de ComPtrRef.  
  
## Comentarios  
 Recupera la dirección de un puntero a la interfaz representada por el objeto actual de ComPtrRef.  
  
## Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [ComPtrRef \(Clase\)](../Topic/ComPtrRef%20Class.md)   
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)