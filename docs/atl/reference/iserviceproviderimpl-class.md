---
title: "IServiceProviderImpl Class | Microsoft Docs"
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
  - "ATL::IServiceProviderImpl<T>"
  - "ATL.IServiceProviderImpl<T>"
  - "ATL.IServiceProviderImpl"
  - "ATL::IServiceProviderImpl"
  - "IServiceProviderImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IServiceProvider (interfaz), implementación de ATL"
  - "IServiceProviderImpl class"
ms.assetid: 251254d3-c4ce-40d7-aee0-3d676d1d72f2
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IServiceProviderImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

esta clase proporciona una implementación predeterminada de la interfaz de `IServiceProvider` .  
  
## Sintaxis  
  
```  
  
      template <  
   class T  
>   
class ATL_NO_VTABLE IServiceProviderImpl :  
   public IServiceProvider  
```  
  
#### Parámetros  
 `T`  
 la clase, derivada de `IServiceProviderImpl`.  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IServiceProviderImpl::QueryService](../Topic/IServiceProviderImpl::QueryService.md)|Crea o tiene acceso al servicio especificado y devuelve un puntero de interfaz a la interfaz especificada para el servicio.|  
  
## Comentarios  
 La interfaz de `IServiceProvider` busca un servicio especificado por su GUID y devuelve el puntero de interfaz para la interfaz solicitada en el servicio.  La clase `IServiceProviderImpl` proporciona una implementación predeterminada de esta interfaz.  
  
 **IServiceProviderImpl** especifica un método: [QueryService](../Topic/IServiceProviderImpl::QueryService.md), creando o tiene acceso al servicio especificado y devuelve un puntero de interfaz a la interfaz especificada para el servicio.  
  
 `IServiceProviderImpl` utiliza un mapa de servicio, empezando por [BEGIN\_SERVICE\_MAP](../Topic/BEGIN_SERVICE_MAP.md) y termina con [END\_SERVICE\_MAP](../Topic/END_SERVICE_MAP.md).  
  
 El mapa del servicio contiene dos entradas: [SERVICE\_ENTRY](../Topic/SERVICE_ENTRY.md), que indica un id. de servicio especificado \(SID\) compatible con el objeto, y [SERVICE\_ENTRY\_CHAIN](../Topic/SERVICE_ENTRY_CHAIN.md), que llama a `QueryService` para encadenar a otro objeto.  
  
## Jerarquía de herencia  
 `IServiceProvider`  
  
 `IServiceProviderImpl`  
  
## Requisitos  
 **encabezado:** atlcom.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)