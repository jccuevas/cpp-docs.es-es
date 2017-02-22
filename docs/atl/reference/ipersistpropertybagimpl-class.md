---
title: "IPersistPropertyBagImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IPersistPropertyBagImpl"
  - "ATL.IPersistPropertyBagImpl<T>"
  - "ATL::IPersistPropertyBagImpl"
  - "ATL::IPersistPropertyBagImpl<T>"
  - "ATL.IPersistPropertyBagImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IPersistPropertyBagImpl class"
ms.assetid: 712af24d-99f8-40f2-9811-53b3ff6e5b19
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# IPersistPropertyBagImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase implementa **IUnknown** y permite que un objeto guarde sus propiedades en un contenedor de propiedades cliente\-proporcionado.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## Sintaxis  
  
```  
  
      template <   
class T   
>  
class ATL_NO_VTABLE IPersistPropertyBagImpl :  
public IPersistPropertyBag  
```  
  
#### Parámetros  
 `T`  
 la clase, derivada de `IPersistPropertyBagImpl`.  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IPersistPropertyBagImpl::GetClassID](../Topic/IPersistPropertyBagImpl::GetClassID.md)|Recupera el CLSID del objeto.|  
|[IPersistPropertyBagImpl::InitNew](../Topic/IPersistPropertyBagImpl::InitNew.md)|Inicializa un objeto recién creado.  la implementación de ATL devuelve `S_OK`.|  
|[IPersistPropertyBagImpl::Load](../Topic/IPersistPropertyBagImpl::Load.md)|Carga las propiedades de objeto de un contenedor de propiedades cliente\-proporcionado.|  
|[IPersistPropertyBagImpl::Save](../Topic/IPersistPropertyBagImpl::Save.md)|Guarda las propiedades del objeto en un contenedor de propiedades cliente\-proporcionado.|  
  
## Comentarios  
 La interfaz de [IPersistPropertyBag](https://msdn.microsoft.com/en-us/library/aa768205.aspx) permite que un objeto guarde sus propiedades en un contenedor de propiedades cliente\-proporcionado.  La clase `IPersistPropertyBagImpl` proporciona una implementación predeterminada de esta interfaz y implementa **IUnknown** enviando información del dispositivo de volcado en versiones de depuración.  
  
 **IPersistPropertyBag** funciona junto con [IPropertyBag](https://msdn.microsoft.com/en-us/library/aa768196.aspx) y [IErrorLog](https://msdn.microsoft.com/en-us/library/aa768231.aspx).  Estas dos últimas interfaces deben implementar por el cliente.  Con `IPropertyBag`, el cliente guarda y carga las propiedades individuales del objeto.  Con **IErrorLog**, el objeto y el cliente pueden notificar cualquier error encontrado.  
  
 **artículos relacionados** [tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [Crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## Jerarquía de herencia  
 `IPersistPropertyBag`  
  
 `IPersistPropertyBagImpl`  
  
## Requisitos  
 **encabezado:** atlcom.h  
  
## Vea también  
 [BEGIN\_PROP\_MAP](../Topic/BEGIN_PROP_MAP.md)   
 [Class Overview](../../atl/atl-class-overview.md)