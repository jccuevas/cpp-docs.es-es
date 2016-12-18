---
title: "BoolStruct (Estructura) | Microsoft Docs"
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
  - "internal/Microsoft::WRL::Details::BoolStruct"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BoolStruct (estructura)"
ms.assetid: 666eae78-e81d-4fb7-a9e4-1ba617d6d4cd
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# BoolStruct (Estructura)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
struct BoolStruct;  
```  
  
## Comentarios  
 La estructura de BoolStruct define si un ComPtr administra la duración de objeto de una interfaz.  BoolStruct es utilizado internamente por el operador de [BoolType\(\)](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md) .  
  
## Miembros  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[BoolStruct::Member \(Miembro de datos\)](../Topic/BoolStruct::Member%20Data%20Member.md)|Especifica que es [ComPtr](../windows/comptr-class.md) , o no, administrar la duración de objeto de una interfaz.|  
  
## Jerarquía de herencia  
 `BoolStruct`  
  
## Requisitos  
 **Encabezado:** internal.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)   
 [ComPtr::operator Microsoft::WRL::Details::BoolType \(Operador\)](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md)