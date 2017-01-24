---
title: "IPersistStorageImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::IPersistStorageImpl"
  - "ATL::IPersistStorageImpl<T>"
  - "ATL.IPersistStorageImpl<T>"
  - "IPersistStorageImpl"
  - "ATL.IPersistStorageImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IPersistStorageImpl class"
  - "almacenamiento, ATL"
ms.assetid: d652f02c-239c-47c7-9a50-3e9fc3014fff
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IPersistStorageImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

esta clase implementa la interfaz de [IPersistStorage](http://msdn.microsoft.com/library/windows/desktop/ms679731) .  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## Sintaxis  
  
```  
  
      template <  
class T  
>  
class ATL_NO_VTABLE IPersistStorageImpl :  
public IPersistStorage  
```  
  
#### Parámetros  
 `T`  
 la clase, derivada de `IPersistStorageImpl`.  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IPersistStorageImpl::GetClassID](../Topic/IPersistStorageImpl::GetClassID.md)|Recupera el CLSID del objeto.|  
|[IPersistStorageImpl::HandsOffStorage](../Topic/IPersistStorageImpl::HandsOffStorage.md)|Indica al objeto para liberar todos los objetos de almacenamiento y para activar el modo de HandsOff.  la implementación de ATL devuelve `S_OK`.|  
|[IPersistStorageImpl::InitNew](../Topic/IPersistStorageImpl::InitNew.md)|Inicializa un nuevo almacén.|  
|[IPersistStorageImpl::IsDirty](../Topic/IPersistStorageImpl::IsDirty.md)|Comprueba si los datos de objeto ha cambiado desde que se guardó por última vez.|  
|[IPersistStorageImpl::Load](../Topic/IPersistStorageImpl::Load.md)|Carga las propiedades del objeto de almacenamiento especificado.|  
|[IPersistStorageImpl::Save](../Topic/IPersistStorageImpl::Save.md)|Guarda las propiedades del objeto al almacén especificado.|  
|[IPersistStorageImpl::SaveCompleted](../Topic/IPersistStorageImpl::SaveCompleted.md)|Notifica a un objeto que puede volver al modo normal para escribir su objeto de almacenamiento.  la implementación de ATL devuelve `S_OK`.|  
  
## Comentarios  
 `IPersistStorageImpl` implementa la interfaz de [IPersistStorage](http://msdn.microsoft.com/library/windows/desktop/ms679731) , que permite que un cliente solicite que la carga del objeto y guardar los datos persistentes mediante un almacenamiento.  
  
 La implementación de esta clase requiere la clase `T` crear una implementación de la interfaz de `IPersistStreamInit` disponible mediante `QueryInterface`.  Esto suele significar que la clase `T` debe derivar de [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md), proporcionar una entrada para `IPersistStreamInit` en [Mapa COM](../Topic/BEGIN_COM_MAP.md), y utilizar [mapa de propiedades](../Topic/BEGIN_PROP_MAP.md) para describir datos persistentes de la clase.  
  
 **artículos relacionados** [tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [Crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## Jerarquía de herencia  
 `IPersistStorage`  
  
 `IPersistStorageImpl`  
  
## Requisitos  
 **encabezado:** atlcom.h  
  
## Vea también  
 [Storages and Streams](http://msdn.microsoft.com/library/windows/desktop/aa380352)   
 [IPersistStreamInitImpl Class](../../atl/reference/ipersiststreaminitimpl-class.md)   
 [IPersistPropertyBagImpl Class](../../atl/reference/ipersistpropertybagimpl-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)