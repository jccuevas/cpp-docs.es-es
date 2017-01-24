---
title: "SyncLockWithStatusT::IsLocked (M&#233;todo) | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::IsLocked"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IsLocked (método)"
ms.assetid: e1b75b7b-c145-471a-aa5d-71abf31f5990
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SyncLockWithStatusT::IsLocked (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
bool IsLocked() const;  
```  
  
## Comentarios  
 Indica si el objeto actual de SyncLockWithStatusT posee un recurso; es decir, el objeto de SyncLockWithStatusT *está bloqueado*.  
  
## Valor devuelto  
 **true** si el objeto de SyncLockWithStatusT está bloqueado; si no, **false**.  
  
## Requisitos  
 **Encabezado:** corewrappers.h  
  
 **Espacio de nombres:** Microsoft::WRL::Wrappers::Details  
  
## Vea también  
 [SyncLockWithStatusT \(Clase\)](../windows/synclockwithstatust-class.md)