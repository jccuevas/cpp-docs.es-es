---
title: "ComPtrRefBase::operator IUnknown** (Operador) | Microsoft Docs"
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
  - "client/Microsoft::WRL::Details::ComPtrRefBase::operator IUnknown**"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator IUnknown** (operador)"
ms.assetid: c2950abf-a7aa-480a-ba41-615703e7f931
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtrRefBase::operator IUnknown** (Operador)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
operator IUnknown**() const;  
```  
  
## Comentarios  
 Convierte el miembro de datos actual de [ptr\_](../windows/comptrrefbase-ptr-data-member.md) a puntero\-a\-uno\-puntero\- a la interfaz IUnknown.  
  
 Se produce un error si el ComPtrRefBase actual no deriva de IUnknown.  
  
## Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [ComPtrRefBase \(Clase\)](../windows/comptrrefbase-class.md)   
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)