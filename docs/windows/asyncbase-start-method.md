---
title: "AsyncBase::Start (M&#233;todo) | Microsoft Docs"
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
  - "async/Microsoft::WRL::AsyncBase::Start"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Start (método)"
ms.assetid: 67405c9d-0d1a-4c1e-8ea4-6ba01c1f90d9
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AsyncBase::Start (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Inicia la operación asincrónica.  
  
## Sintaxis  
  
```  
STDMETHOD(  
   Start  
)(void);  
```  
  
## Valor devuelto  
 S\_OK si la operación se inicia o se inicia ya; si no, E\_ILLEGAL\_STATE\_CHANGE.  
  
## Comentarios  
 Start\(\) es una implementación predeterminada de IAsyncInfo::Start, y no tiene ningún trabajo.  Para iniciar realmente una operación asincrónica, invalide el método virtual pura de OnStart\(\) .  
  
## Requisitos  
 **Encabezado:** async.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [AsyncBase \(Clase\)](../windows/asyncbase-class.md)