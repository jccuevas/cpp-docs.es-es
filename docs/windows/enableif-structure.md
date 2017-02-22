---
title: "EnableIf (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "internal/Microsoft::WRL::Details::EnableIf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "EnableIf (estructura)"
ms.assetid: 7825b283-e6b2-4f39-a4b9-c03bcd431b8e
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# EnableIf (Estructura)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
template <  
   bool b,  
   typename T = void  
>  
  
struct EnableIf;  
template <  
   typename T  
>  
struct EnableIf<true, T>;  
```  
  
#### Parámetros  
 `T`  
 Un tipo.  
  
 `b`  
 Expresión booleana.  
  
## Comentarios  
 Define un miembro de datos del tipo especificado por el segundo parámetro de plantilla si el primer parámetro de plantilla se evalúa como `true`.  
  
## Miembros  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`type`|Si el parámetro `b` de plantilla se evalúa como `true`, la especialización parcial define el miembro de datos `type` para ser de `T`escrito.|  
  
## Jerarquía de herencia  
 `EnableIf`  
  
## Requisitos  
 **Encabezado:** internal.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)