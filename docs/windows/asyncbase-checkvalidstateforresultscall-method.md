---
title: "AsyncBase::CheckValidStateForResultsCall (M&#233;todo) | Microsoft Docs"
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
  - "async/Microsoft::WRL::AsyncBase::CheckValidStateForResultsCall"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CheckValidStateForResultsCall (método)"
ms.assetid: 87ca6805-bff1-4063-b855-6dd26132deff
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AsyncBase::CheckValidStateForResultsCall (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comprueba si los resultados de una operación asincrónica se pueden obtener en estado asincrónica actual.  
  
## Sintaxis  
  
```  
inline HRESULT CheckValidStateForResultsCall();  
```  
  
## Valor devuelto  
 S\_OK si los resultados se pueden recopilar; si no, E\_ILLEGAL\_METHOD\_CALLE\_ILLEGAL\_METHOD\_CALL.  
  
## Requisitos  
 **Encabezado:** async.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [AsyncBase \(Clase\)](../windows/asyncbase-class.md)