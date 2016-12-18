---
title: "ComPtrRefBase::operator IInspectable** (Operador) | Microsoft Docs"
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
  - "client/Microsoft::WRL::Details::ComPtrRefBase::operator IInspectable**"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator IInspectable** (operador)"
ms.assetid: 06ac1051-606c-449b-a566-cac78ca53762
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtrRefBase::operator IInspectable** (Operador)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
operator IInspectable**() const;  
```  
  
## Comentarios  
 Convierte el miembro de datos actual de [ptr\_](../windows/comptrrefbase-ptr-data-member.md) a puntero\-a\-uno\-puntero\- a la interfaz de IInspectable.  
  
 Se produce un error si el ComPtrRefBase actual no se deriva de IInspectable.  
  
 Esta conversión solo está disponible si se define **\_\_WRL\_CLASSIC\_COM\_\_** .  
  
## Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [ComPtrRefBase \(Clase\)](../windows/comptrrefbase-class.md)   
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)