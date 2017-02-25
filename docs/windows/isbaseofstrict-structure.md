---
title: "IsBaseOfStrict (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "internal/Microsoft::WRL::Details::IsBaseOfStrict"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IsBaseOfStrict (estructura)"
ms.assetid: 6fed7366-c8d4-4991-b4fb-43ed93f8e1bf
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# IsBaseOfStrict (Estructura)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
template <  
   typename Base,  
   typename Derived  
>  
  
struct IsBaseOfStrict;  
template <  
   typename Base  
>  
struct IsBaseOfStrict<Base, Base>;  
```  
  
#### Parámetros  
 `Base`  
 Tipo base.  
  
 `Derived`  
 El tipo derivado.  
  
## Comentarios  
 Comprueba si un tipo es la base de otro.  
  
 La primera plantilla prueba si derivan a un tipo de un tipo base, lo que puede provocar **true** o **false**.  La segunda plantilla prueba si derivan a un tipo de sí mismo, que siempre **false**.  
  
## Miembros  
  
### Constantes públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[IsBaseOfStrict::value \(Constante\)](../Topic/IsBaseOfStrict::value%20Constant.md)|Indica si un tipo es la base de otro.|  
  
## Jerarquía de herencia  
 `IsBaseOfStrict`  
  
## Requisitos  
 **Encabezado:** internal.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)