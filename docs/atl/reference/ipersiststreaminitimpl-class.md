---
title: "IPersistStreamInitImpl Class | Microsoft Docs"
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
  - "ATL::IPersistStreamInitImpl"
  - "ATL::IPersistStreamInitImpl<T>"
  - "ATL.IPersistStreamInitImpl<T>"
  - "IPersistStreamInitImpl"
  - "ATL.IPersistStreamInitImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IPersistStreamInit ATL implementation"
  - "IPersistStreamInitImpl class"
  - "secuencias, ATL"
ms.assetid: ef217c3c-020f-4cf8-871e-ef68e57865b8
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IPersistStreamInitImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

esta clase implementa **IUnknown** y proporciona una implementación predeterminada de la interfaz de [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) .  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## Sintaxis  
  
```  
  
      template<  
class T   
>  
class ATL_NO_VTABLE IPersistStreamInitImpl :  
public IPersistStreamInit  
```  
  
#### Parámetros  
 `T`  
 la clase, derivada de `IPersistStreamInitImpl`.  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IPersistStreamInitImpl::GetClassID](../Topic/IPersistStreamInitImpl::GetClassID.md)|Recupera el CLSID del objeto.|  
|[IPersistStreamInitImpl::GetSizeMax](../Topic/IPersistStreamInitImpl::GetSizeMax.md)|Recupera el tamaño de la secuencia necesaria para guardar los datos de objeto.  la implementación de ATL devuelve **E\_NOTIMPL**.|  
|[IPersistStreamInitImpl::InitNew](../Topic/IPersistStreamInitImpl::InitNew.md)|Inicializa un objeto recién creado.|  
|[IPersistStreamInitImpl::IsDirty](../Topic/IPersistStreamInitImpl::IsDirty.md)|Comprueba si los datos de objeto ha cambiado desde que se guardó por última vez.|  
|[IPersistStreamInitImpl::Load](../Topic/IPersistStreamInitImpl::Load.md)|Carga las propiedades del objeto de la secuencia especificada.|  
|[IPersistStreamInitImpl::Save](../Topic/IPersistStreamInitImpl::Save.md)|Guarda las propiedades de objeto en la secuencia especificada.|  
  
## Comentarios  
 La interfaz de [IPersistStreamInit](http://msdn.microsoft.com/library/windows/desktop/ms682273) permite que un cliente solicite que el objeto cargue y guarde los datos persistentes a una sola secuencia.  La clase `IPersistStreamInitImpl` proporciona una implementación predeterminada de esta interfaz y implementa **IUnknown** enviando información del dispositivo de volcado en versiones de depuración.  
  
 **artículos relacionados** [tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [Crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## Jerarquía de herencia  
 `IPersistStreamInit`  
  
 `IPersistStreamInitImpl`  
  
## Requisitos  
 **encabezado:** atlcom.h  
  
## Vea también  
 [Storages and Streams](http://msdn.microsoft.com/library/windows/desktop/aa380352)   
 [Class Overview](../../atl/atl-class-overview.md)