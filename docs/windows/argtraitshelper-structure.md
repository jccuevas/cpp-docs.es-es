---
title: "ArgTraitsHelper (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "event/Microsoft::WRL::Details::ArgTraitsHelper"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ArgTraitsHelper (estructura)"
ms.assetid: e3f798da-0aef-4a57-95d3-d38c34c47d72
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# ArgTraitsHelper (Estructura)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
template<  
   typename TDelegateInterface  
>  
struct ArgTraitsHelper;  
```  
  
#### Parámetros  
 `TDelegateInterface`  
 Una interfaz de delegado.  
  
## Comentarios  
 Ayuda a definir características comunes de los argumentos de delegado.  
  
## Miembros  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`methodType`|Sinónimo de `decltype(&TDelegateInterface::Invoke)`.|  
|`Traits`|Sinónimo de `ArgTraits<methodType>`.|  
  
### Constantes públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[ArgTraitsHelper::args \(Constante\)](../windows/argtraitshelper-args-constant.md)|Ayuda [ArgTraits::args](../windows/argtraits-args-constant.md) conservan el recuento del número de parámetros del método invoke de una interfaz de delegado.|  
  
## Jerarquía de herencia  
 `ArgTraitsHelper`  
  
## Requisitos  
 **Encabezado:** event.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)