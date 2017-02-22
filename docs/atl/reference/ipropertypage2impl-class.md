---
title: "IPropertyPage2Impl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IPropertyPage2Impl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IPropertyPage2 ATL implementation"
  - "IPropertyPage2Impl class"
  - "páginas de propiedades"
ms.assetid: e89fbe90-203a-47f0-a5de-23616697e1ce
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# IPropertyPage2Impl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

esta clase implementa **IUnknown** y hereda la implementación predeterminada de [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md).  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## Sintaxis  
  
```  
  
      template< class   
      T  
      >  
class IPropertyPage2Impl : public IPropertyPageImpl< T>  
```  
  
#### Parámetros  
 `T`  
 la clase, derivada de `IPropertyPage2Impl`.  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IPropertyPage2Impl::EditProperty](../Topic/IPropertyPage2Impl::EditProperty.md)|Especifica que el control de la propiedad recibirá el foco cuando se activa la página de propiedades.  la implementación de ATL devuelve **E\_NOTIMPL**.|  
  
## Comentarios  
 la interfaz de [IPropertyPage2](http://msdn.microsoft.com/library/windows/desktop/ms683996) extiende [IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246) agregando el método de `EditProperty` .  Este método permite que un cliente seleccione una propiedad específica en un objeto de la página de propiedades.  
  
 La clase `IPropertyPage2Impl` simplemente devuelve **E\_NOTIMPL** para **IPropertyPage2:: EditProperty**.  Sin embargo, hereda la implementación predeterminada de [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md) e implementa **IUnknown** enviando información del dispositivo de volcado en versiones de depuración.  
  
 Cuando se crea una página de propiedades, la clase es normalmente derivada de `IPropertyPageImpl`.  Proporcionar compatibilidad adicional de **IPropertyPage2**, modifique la definición de clase y reemplace el método de `EditProperty` .  
  
 **artículos relacionados** [tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [Crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## Jerarquía de herencia  
 `IPropertyPage`  
  
 [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)  
  
 `IPropertyPage2Impl`  
  
## Requisitos  
 **encabezado:** atlctl.h  
  
## Vea también  
 [IPerPropertyBrowsingImpl Class](../../atl/reference/iperpropertybrowsingimpl-class.md)   
 [ISpecifyPropertyPagesImpl Class](../../atl/reference/ispecifypropertypagesimpl-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)