---
title: "IConnectionPointContainerImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::IConnectionPointContainerImpl"
  - "ATL.IConnectionPointContainerImpl"
  - "ATL.IConnectionPointContainerImpl<T>"
  - "IConnectionPointContainerImpl"
  - "ATL::IConnectionPointContainerImpl<T>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "connectable objects"
  - "puntos de conexión [C++], container"
  - "IConnectionPointContainerImpl class"
ms.assetid: 10db5a8d-8be9-4d9d-8a82-8ab9ffe3e9d6
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# IConnectionPointContainerImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase implementa un contenedor de punto de conexión para administrar una colección de objetos [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) .  
  
## Sintaxis  
  
```  
  
      template<  
   class T   
>  
class ATL_NO_VTABLE IConnectionPointContainerImpl :   
   public IConnectionPointContainer  
```  
  
#### Parámetros  
 `T`  
 la clase, derivada de `IConnectionPointContainerImpl`.  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IConnectionPointContainerImpl::EnumConnectionPoints](../Topic/IConnectionPointContainerImpl::EnumConnectionPoints.md)|Crea un enumerador para recorrer en iteración los puntos de conexión admitidos en el objeto conectable.|  
|[IConnectionPointContainerImpl::FindConnectionPoint](../Topic/IConnectionPointContainerImpl::FindConnectionPoint.md)|Recupera un puntero de interfaz al punto de conexión que admite el IID especificado.|  
  
## Comentarios  
 `IConnectionPointContainerImpl` implementa un contenedor de punto de conexión para administrar una colección de objetos [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md) .  `IConnectionPointContainerImpl` proporciona dos métodos que un cliente puede llamar para recuperar más información sobre un objeto conectable:  
  
-   `EnumConnectionPoints` permite al cliente determinar que las interfaces de salida el objeto admiten.  
  
-   `FindConnectionPoint` permite al cliente determinar si el objeto admite una interfaz de salida concreta.  
  
 Para obtener información sobre cómo utilizar los puntos de conexión en ATL, vea el artículo [Puntos de conexión](../../atl/atl-connection-points.md).  
  
## Jerarquía de herencia  
 `IConnectionPointContainer`  
  
 `IConnectionPointContainerImpl`  
  
## Requisitos  
 **encabezado:** atlcom.h  
  
## Vea también  
 [IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857)   
 [Class Overview](../../atl/atl-class-overview.md)