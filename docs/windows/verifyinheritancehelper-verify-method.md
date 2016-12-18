---
title: "VerifyInheritanceHelper::Verify (M&#233;todo) | Microsoft Docs"
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
  - "implements/Microsoft::WRL::Details::VerifyInheritanceHelper::Verify"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Verify (método)"
ms.assetid: 3360082b-81ad-4191-9ec3-b4372f7207d7
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# VerifyInheritanceHelper::Verify (M&#233;todo)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
static void Verify();  
```  
  
## Comentarios  
 Prueba las dos interfaces especificadas por los parámetros actuales de la plantilla y determina si una interfaz se deriva de la otra.  
  
 Se produce un error si una interfaz no se deriva de otro.  
  
## Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [VerifyInheritanceHelper \(Estructura\)](../windows/verifyinheritancehelper-structure.md)   
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)