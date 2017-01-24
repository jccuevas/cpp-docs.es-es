---
title: "ActivationFactory::Release (M&#233;todo) | Microsoft Docs"
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
  - "module/Microsoft::WRL::ActivationFactory::Release"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Release (método)"
ms.assetid: 5bc25ff0-ee3c-4a2d-a9b6-2d8f158033ad
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ActivationFactory::Release (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Disminuye el recuento de referencias del objeto actual de ActivationFactory.  
  
## Sintaxis  
  
```  
STDMETHOD_(  
   ULONG,  
   Release  
)();  
```  
  
## Valor devuelto  
 S\_OK si correctamente; si no, un HRESULT que describe el error.  
  
## Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [ActivationFactory \(Clase\)](../windows/activationfactory-class.md)