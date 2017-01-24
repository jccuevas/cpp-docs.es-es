---
title: "VerifyInterfaceHelper (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::VerifyInterfaceHelper"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VerifyInterfaceHelper (estructura)"
ms.assetid: ea95b641-199a-4fdf-964b-186b40cb3ba7
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# VerifyInterfaceHelper (Estructura)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Es compatible con la infraestructura de [!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)] y no está diseñado para que se utilice directamente desde el código.  
  
## Sintaxis  
  
```  
template <  
   bool isWinRTInterface,  
   typename I  
>  
struct VerifyInterfaceHelper;  
  
template <  
   typename I  
>  
struct VerifyInterfaceHelper<false, I>;  
```  
  
#### Parámetros  
 `I`  
 Una interfaz a comprobar.  
  
 `isWinRTInterface`  
  
## Comentarios  
 Comprueba que la interfaz especificada por el parámetro de plantilla cumpla ciertos requisitos.  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[VerifyInterfaceHelper::Verify \(Método\)](../windows/verifyinterfacehelper-verify-method.md)||  
  
## Jerarquía de herencia  
 `VerifyInterfaceHelper`  
  
## Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)