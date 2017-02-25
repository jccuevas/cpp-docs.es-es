---
title: "ImplementsHelper (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "implements/Microsoft::WRL::Details::ImplementsHelper"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ImplementsHelper (estructura)"
ms.assetid: b857ba80-81bd-4e53-92b6-210991954243
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# ImplementsHelper (Estructura)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Admite la infraestructura de WRL y no está diseñado para usarse directamente desde el código.  
  
## Sintaxis  
  
```  
template <  
   typename RuntimeClassFlagsT,  
   typename ILst,  
   bool IsDelegateToClass  
>  
friend struct Details::ImplementsHelper;  
```  
  
#### Parámetros  
 `RuntimeClassFlagsT`  
 Un campo de marcas que especificar uno o varios enumeradores de [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) .  
  
 `ILst`  
 Una lista de id. de la interfaz.  
  
 `IsDelegateToClass`  
 Especifique `true` si la instancia actual de implementa es una clase base del primer identificador de interfaz en `ILst`; si no, `false`.  
  
## Comentarios  
 Ayuda implementan la estructura de [Implementa](../Topic/Implements%20Structure.md) .  
  
 Esta plantilla recorrer la lista de interfaces y los agrega como clases base, como información necesaria para habilitar QueryInterface.  
  
## Miembros  
  
## Jerarquía de herencia  
 `ImplementsHelper`  
  
## Requisitos  
 **Encabezado:** implements.h  
  
 **Espacio de nombres:** Microsoft::WRL::Details  
  
## Vea también  
 [Reference \(Windows Runtime Library\)](http://msdn.microsoft.com/es-es/00000000-0000-0000-0000-000000000000)   
 [Microsoft::WRL::Details \(Espacio de nombres\)](../windows/microsoft-wrl-details-namespace.md)