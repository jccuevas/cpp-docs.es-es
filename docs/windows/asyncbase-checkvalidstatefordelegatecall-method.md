---
title: "AsyncBase::CheckValidStateForDelegateCall (M&#233;todo) | Microsoft Docs"
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
  - "async/Microsoft::WRL::AsyncBase::CheckValidStateForDelegateCall"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CheckValidStateForDelegateCall (método)"
ms.assetid: d997ebe7-2378-4e74-a379-f0f85e6922f0
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AsyncBase::CheckValidStateForDelegateCall (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comprueba si las propiedades del delegado se pueden modificar en el estado asincrónica actual.  
  
## Sintaxis  
  
```  
inline HRESULT CheckValidStateForDelegateCall();  
```  
  
## Valor devuelto  
 S\_OK si las propiedades de delegado pueden modificar; si no, E\_ILLEGAL\_METHOD\_CALL.  
  
## Requisitos  
 **Encabezado:** async.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [AsyncBase \(Clase\)](../windows/asyncbase-class.md)