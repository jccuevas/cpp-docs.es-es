---
title: "VerifyInheritanceHelper (Estructura) | Microsoft Docs"
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
  - "implements/Microsoft::WRL::Details::VerifyInheritanceHelper"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VerifyInheritanceHelper (estructura)"
ms.assetid: 8a48a702-0f71-4807-935b-8311f0a7a8b6
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# VerifyInheritanceHelper (Estructura)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
template <  
   typename I,  
   typename Base  
>  
struct VerifyInheritanceHelper;  
template <  
   typename I  
>  
struct VerifyInheritanceHelper<I, Nil>;  
```  
  
#### Parámetros  
 `I`  
 Un tipo.  
  
 `Base`  
 Otro.  
  
## Comentarios  
 Comprueba si una interfaz se deriva de otra interfaz.  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[VerifyInheritanceHelper::Verify \(Método\)](../windows/verifyinheritancehelper-verify-method.md)|Prueba las dos interfaces especificadas por los parámetros actuales de la plantilla y determina si una interfaz se deriva de la otra.|  
  
## Jerarquía de herencia  
 `VerifyInheritanceHelper`  
  
## Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)