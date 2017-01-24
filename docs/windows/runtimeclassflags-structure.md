---
title: "RuntimeClassFlags (Estructura) | Microsoft Docs"
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
  - "implements/Microsoft::WRL::RuntimeClassFlags"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RuntimeClassFlags (estructura)"
ms.assetid: 7098d605-bd14-4d51-82f4-3def8296a938
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# RuntimeClassFlags (Estructura)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Contiene el tipo de una instancia de [RuntimeClass](../windows/runtimeclass-class.md).  
  
## Sintaxis  
  
```  
template <  
   unsigned int flags  
>  
struct RuntimeClassFlags;  
```  
  
#### Parámetros  
 `flags`  
 Valor [RuntimeClassType \(Enumeración\)](../windows/runtimeclasstype-enumeration.md).  
  
## Miembros  
  
### Constantes públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[RuntimeClassFlags::value \(Constante\)](../windows/runtimeclassflags-value-constant.md)|Contiene un valor de [RuntimeClassType \(Enumeración\)](../windows/runtimeclasstype-enumeration.md) .|  
  
## Jerarquía de herencia  
 `RuntimeClassFlags`  
  
## Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## Vea también  
 [Microsoft::WRL \(Espacio de nombres\)](../windows/microsoft-wrl-namespace.md)