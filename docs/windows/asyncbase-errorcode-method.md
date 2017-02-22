---
title: "AsyncBase::ErrorCode (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "async/Microsoft::WRL::AsyncBase::ErrorCode"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ErrorCode (método)"
ms.assetid: 3f5f0f69-d60a-4a67-8cc6-a55fdc89a192
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# AsyncBase::ErrorCode (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Recupera el código de error para la operación asincrónica actual.  
  
## Sintaxis  
  
```  
inline void ErrorCode(  
   HRESULT *error  
);  
```  
  
#### Parámetros  
 `error`  
 La ubicación donde esta operación almacena el código de error actual.  
  
## Comentarios  
 Esta operación es seguro para subprocesos.  
  
## Requisitos  
 **Encabezado:** async.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [AsyncBase \(Clase\)](../windows/asyncbase-class.md)