---
title: "AsyncBase::FireProgress (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "async/Microsoft::WRL::AsyncBase::FireProgress"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "FireProgress (método)"
ms.assetid: 4512bef6-0ebc-4465-9b8a-4c9dfa82084c
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# AsyncBase::FireProgress (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Invoca el controlador de eventos actual de progreso.  
  
## Sintaxis  
  
```  
void FireProgress(  
   const typename ProgressTraits::Arg2Type arg  
);  
```  
  
#### Parámetros  
 `arg`  
 El método de control de eventos a invocar.  
  
## Comentarios  
 `ProgressTraits` se deriva de [ArgTraitsHelper \(Estructura\)](../windows/argtraitshelper-structure.md).  
  
## Requisitos  
 **Encabezado:** async.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [AsyncBase \(Clase\)](../windows/asyncbase-class.md)