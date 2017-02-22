---
title: "ActivationFactory::AddRef (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::ActivationFactory::AddRef"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddRef (método)"
ms.assetid: dfe96189-ddbe-410a-9f8d-5d8ecc8cc7e6
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# ActivationFactory::AddRef (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Incrementa el recuento de referencias del objeto actual de ActivationFactory.  
  
## Sintaxis  
  
```  
STDMETHOD_(  
   ULONG,  
   AddRef  
)();  
```  
  
## Valor devuelto  
 S\_OK si correctamente; si no, un HRESULT que describe el error.  
  
## Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [ActivationFactory \(Clase\)](../windows/activationfactory-class.md)