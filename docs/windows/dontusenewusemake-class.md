---
title: "DontUseNewUseMake (Clase) | Microsoft Docs"
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
  - "implements/Microsoft::WRL::Details::DontUseNewUseMake"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DontUseNewUseMake (clase)"
ms.assetid: 8b38d07b-fc14-4cea-afb9-4c1a7dde0093
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# DontUseNewUseMake (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
class DontUseNewUseMake;  
```  
  
## Comentarios  
 Evita mediante el operador `new` en RuntimeClass.  Por consiguiente, debe utilizar [Cree la función](../windows/make-function.md) en su lugar.  
  
## Miembros  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[DontUseNewUseMake::operator new \(Operador\)](../windows/dontusenewusemake-operator-new-operator.md)|Sobrecarga el operador `new` y evita que se utilizan en RuntimeClass.|  
  
## Jerarquía de herencia  
 `DontUseNewUseMake`  
  
## Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)   
 [Make \(Función\)](../windows/make-function.md)