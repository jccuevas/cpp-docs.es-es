---
title: "ActivationFactory::GetIids (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::ActivationFactory::GetIids"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetIids (método)"
ms.assetid: 0983d709-d155-4d65-aae4-5b2c8bb0fede
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# ActivationFactory::GetIids (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Recupera una matriz de id. implementados de la interfaz.  
  
## Sintaxis  
  
```  
STDMETHOD(  
   GetIids  
)(_Out_ ULONG *iidCount, _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);  
```  
  
#### Parámetros  
 `iidCount`  
 Cuando esta operación finaliza, el número de id. de interace en la matriz de `iids` .  
  
 `iids`  
 Cuando esta operación finaliza, una matriz de id. implementados de la interfaz.  
  
## Valor devuelto  
 S\_OK si correctamente; si no, un HRESULT que describe el error.  E\_OUTOFMEMORY es un posible error HRESULT.  
  
## Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [ActivationFactory \(Clase\)](../windows/activationfactory-class.md)