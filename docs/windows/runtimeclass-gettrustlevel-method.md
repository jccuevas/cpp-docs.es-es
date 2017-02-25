---
title: "RuntimeClass::GetTrustLevel (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::RuntimeClass::GetTrustLevel"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetTrustLevel (método)"
ms.assetid: bd90407e-6dd7-41c3-9ea0-c402c276014a
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# RuntimeClass::GetTrustLevel (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Obtiene el nivel de confianza del objeto actual de RuntimeClass.  
  
## Sintaxis  
  
```  
STDMETHOD(  
   GetTrustLevel  
)(_Out_ TrustLevel* trustLvl);  
```  
  
## Parámetros  
 `trustLvl`  
 Cuando esta operación finaliza, el nivel de confianza del objeto actual de RuntimeClass.  
  
## Valor devuelto  
 Siempre S\_OK.  
  
## Comentarios  
 Se produce un error validar si el \_\_WRL\_FORCE\_INSPECTABLE\_CLASS\_MACRO de \_\_WRL\_STRICT\_\_or no está definido.  
  
## Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [RuntimeClass \(Clase\)](../windows/runtimeclass-class.md)