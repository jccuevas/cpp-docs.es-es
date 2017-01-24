---
title: "ActivationFactory::GetTrustLevel (M&#233;todo) | Microsoft Docs"
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
  - "module/Microsoft::WRL::ActivationFactory::GetTrustLevel"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetTrustLevel (método)"
ms.assetid: 31547ae6-d2ab-4039-923c-154d53fb1a8b
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ActivationFactory::GetTrustLevel (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Obtiene el nivel de confianza del objeto que el ActivationFactory actual crea instancias.  
  
## Sintaxis  
  
```  
STDMETHOD(  
   GetTrustLevel  
)(_Out_ TrustLevel* trustLvl);  
```  
  
#### Parámetros  
 `trustLvl`  
 Cuando esta operación finaliza, el nivel de confianza de la clase en tiempo de ejecución que el ActivationFactory crea instancias.  
  
## Valor devuelto  
 S\_OK si correctamente; si no, se produce un error de aserción y `trustLvl` se establece en FullTrust.  
  
## Requisitos  
 **Encabezado:** module.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [ActivationFactory \(Clase\)](../windows/activationfactory-class.md)