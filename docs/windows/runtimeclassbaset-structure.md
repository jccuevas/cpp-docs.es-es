---
title: "RuntimeClassBaseT (Estructura) | Microsoft Docs"
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
  - "implements/Microsoft::WRL::Details::RuntimeClassBaseT"
dev_langs: 
  - "C++"
ms.assetid: a62775fb-3359-4f45-9ff1-c07fa8da464b
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# RuntimeClassBaseT (Estructura)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
template <  
   unsigned int RuntimeClassTypeT  
>  
friend struct Details::RuntimeClassBaseT;  
```  
  
#### Parámetros  
 `RuntimeClassTypeT`  
 Un campo de marcas que especificar uno o varios enumeradores de [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) .  
  
## Comentarios  
 Proporciona métodos auxiliares para operaciones y obtener de `QueryInterface` id. de la interfaz.  
  
## Miembros  
  
## Jerarquía de herencia  
 `RuntimeClassBaseT`  
  
## Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [Reference \(Windows Runtime Library\)](http://msdn.microsoft.com/es-es/00000000-0000-0000-0000-000000000000)   
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)