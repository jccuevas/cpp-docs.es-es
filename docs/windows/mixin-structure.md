---
title: "MixIn (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::MixIn"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MixIn (estructura)"
ms.assetid: 47e2df9b-3a2e-4ae8-8ba3-b1fd3aa73566
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MixIn (Estructura)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Garantiza que una clase en tiempo de ejecución deriva de las interfaces de [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] , si existen, y después de las interfaces COM clásicas.  
  
## Sintaxis  
  
```  
template<  
   typename Derived,  
   typename MixInType,  
   bool hasImplements = __is_base_of(Details::ImplementsBase,  
   MixInType)  
>  
struct MixIn;  
```  
  
#### Parámetros  
 `Derived`  
 Un tipo derivado de la estructura de [Implementa](../Topic/Implements%20Structure.md) .  
  
 `MixInType`  
 Tipo base.  
  
 `hasImplements`  
 `true` si `MixInType` se deriva de la implementación actual el tipo base; `false` de otra manera.  
  
## Comentarios  
 Si una clase derivada de ambos [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] e interfaces COM de la clase, la lista de la declaración de clase debe enumerar cualquier interfaz de [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] y después las interfaces COM clásicas.  MixIn garantiza que las interfaces se especifiquen en el orden correcto.  
  
## Jerarquía de herencia  
 `MixIn`  
  
## Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [Microsoft::WRL \(Espacio de nombres\)](../windows/microsoft-wrl-namespace.md)