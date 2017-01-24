---
title: "AsyncBase::Close (M&#233;todo) | Microsoft Docs"
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
  - "async/Microsoft::WRL::AsyncBase::Close"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Close (método)"
ms.assetid: a52b1124-754b-4393-b491-64aae0c22f1c
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AsyncBase::Close (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cierre la operación asincrónica.  
  
## Sintaxis  
  
```  
STDMETHOD(  
   Close  
)(void) override;  
```  
  
## Valor devuelto  
 S\_OK si la operación cierra o cierra ya; si no, E\_ILLEGAL\_STATE\_CHANGE.  
  
## Comentarios  
 Close\(\) es una implementación predeterminada de IAsyncInfo::Close, y no tiene ningún trabajo.  Para cerrar realmente una operación asincrónica, invalide el método virtual pura de OnClose\(\) .  
  
## Requisitos  
 **Encabezado:** async.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [AsyncBase \(Clase\)](../windows/asyncbase-class.md)