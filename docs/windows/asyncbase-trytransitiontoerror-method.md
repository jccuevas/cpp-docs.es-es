---
title: "AsyncBase::TryTransitionToError (M&#233;todo) | Microsoft Docs"
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
  - "async/Microsoft::WRL::AsyncBase::TryTransitionToError"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "TryTransitionToError (método)"
ms.assetid: f6d11c25-1ce3-43f9-af1c-97c4dc0f6f0f
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AsyncBase::TryTransitionToError (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Indica si el código de error especificado puede modificar el estado de error interno.  
  
## Sintaxis  
  
```  
bool TryTransitionToError(  
   const HRESULT error  
);  
```  
  
#### Parámetros  
 `error`  
 Un error HRESULT.  
  
## Valor devuelto  
 `true` si se cambió el estado de error interno; si no, `false`.  
  
## Comentarios  
 Esta operación modifica el estado de error solo si se establece el estado de error ya a S\_OK.  Esta operación no tiene ningún efecto si el estado del error ya es error, cancela, completado, o cerrado.  
  
## Requisitos  
 **Encabezado:** async.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [AsyncBase \(Clase\)](../windows/asyncbase-class.md)