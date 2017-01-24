---
title: "ClassFactory::Release (M&#233;todo) | Microsoft Docs"
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
  - "module/Microsoft::WRL::ClassFactory::Release"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Release (método)"
ms.assetid: 49da2002-f9d6-4d7f-8a65-48c20b1bf99f
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ClassFactory::Release (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Disminuye el recuento de referencias para el objeto actual de ClassFactory.  
  
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
 [ClassFactory \(Clase\)](../windows/classfactory-class.md)