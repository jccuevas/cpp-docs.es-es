---
title: "SyncLockT::IsLocked (M&#233;todo) | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::IsLocked"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IsLocked (método)"
ms.assetid: a81fea43-f99a-4708-812a-7fd6af500d3d
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SyncLockT::IsLocked (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
bool IsLocked() const;  
```  
  
## Valor devuelto  
 **true** si el objeto de SyncLockT está bloqueado; si no, **false**.  
  
## Comentarios  
 Indica si el objeto actual de SyncLockT posee un recurso; es decir, el objeto de SyncLockT *está bloqueado*.  
  
## Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Microsoft::WRL::Wrappers::Details  
  
## Vea también  
 [SyncLockT \(Clase\)](../windows/synclockt-class.md)