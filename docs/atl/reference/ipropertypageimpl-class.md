---
title: "IPropertyPageImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IPropertyPageImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IPropertyPage ATL implementation"
  - "IPropertyPageImpl class"
  - "páginas de propiedades"
ms.assetid: f9b7c8b1-7a04-4eab-aa63-63efddb740fa
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# IPropertyPageImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

esta clase implementa **IUnknown** y proporciona una implementación predeterminada de la interfaz de [IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246) .  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## Sintaxis  
  
```  
  
      template< class   
      T  
      >  
class IPropertyPageImpl  
```  
  
#### Parámetros  
 `T`  
 la clase, derivada de `IPropertyPageImpl`.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IPropertyPageImpl::IPropertyPageImpl](../Topic/IPropertyPageImpl::IPropertyPageImpl.md)|Constructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IPropertyPageImpl::Activate](../Topic/IPropertyPageImpl::Activate.md)|Crea la ventana cuadro de diálogo de la página de propiedades.|  
|[IPropertyPageImpl::Apply](../Topic/IPropertyPageImpl::Apply.md)|Se aplican los valores actuales de la página de propiedades a los objetos subyacentes especificados con `SetObjects`.  la implementación de ATL devuelve `S_OK`.|  
|[IPropertyPageImpl::Deactivate](../Topic/IPropertyPageImpl::Deactivate.md)|destruye la ventana creada con **Activar**.|  
|[IPropertyPageImpl::GetPageInfo](../Topic/IPropertyPageImpl::GetPageInfo.md)|Recupera información sobre la página de propiedades.|  
|[IPropertyPageImpl::Help](../Topic/IPropertyPageImpl::Help.md)|invoca la ayuda de Windows para la página de propiedades.|  
|[IPropertyPageImpl::IsPageDirty](../Topic/IPropertyPageImpl::IsPageDirty.md)|Indica si la página de propiedades ha cambiado desde que se activa.|  
|[IPropertyPageImpl::Move](../Topic/IPropertyPageImpl::Move.md)|Las posiciones y cambiar el tamaño del cuadro de diálogo página de propiedades.|  
|[IPropertyPageImpl::SetDirty](../Topic/IPropertyPageImpl::SetDirty.md)|Marca el estado de la página de propiedades como cambiado o sin modificar.|  
|[IPropertyPageImpl::SetObjects](../Topic/IPropertyPageImpl::SetObjects.md)|Proporciona una matriz de punteros de **IUnknown** para objetos asociado a la página de propiedades.  estos objetos reciben los valores actuales de la página de propiedades con una llamada a **Aplicar**.|  
|[IPropertyPageImpl::SetPageSite](../Topic/IPropertyPageImpl::SetPageSite.md)|Proporciona la página de propiedades con un puntero de `IPropertyPageSite` , en el que la página de propiedades se comunica con el cuadro de la propiedad.|  
|[IPropertyPageImpl::Show](../Topic/IPropertyPageImpl::Show.md)|Hace que el cuadro de diálogo página de propiedades visible o invisible.|  
|[IPropertyPageImpl::TranslateAccelerator](../Topic/IPropertyPageImpl::TranslateAccelerator.md)|Procesa una tecla especificada.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IPropertyPageImpl::m\_bDirty](../Topic/IPropertyPageImpl::m_bDirty.md)|Especifica si el estado de la página de propiedades ha cambiado.|  
|[IPropertyPageImpl:: el m\_dwDocString](../Topic/IPropertyPageImpl::m_dwDocString.md)|Almacena el identificador de recursos asociado con la cadena de texto que describe la página de propiedades.|  
|[IPropertyPageImpl::m\_dwHelpContext](../Topic/IPropertyPageImpl::m_dwHelpContext.md)|Almacena el identificador del contexto para el tema de Ayuda asociado a la página de propiedades.|  
|[IPropertyPageImpl:: m\_dwHelpFile](../Topic/IPropertyPageImpl::m_dwHelpFile.md)|Almacena el identificador de recursos asociados con el nombre del archivo de ayuda que describe la página de propiedades.|  
|[IPropertyPageImpl:: m\_dwTitle](../Topic/IPropertyPageImpl::m_dwTitle.md)|Almacena el identificador de recursos asociado con la cadena de texto que aparece en la pestaña de la página de propiedades.|  
|[IPropertyPageImpl::m\_nObjects](../Topic/IPropertyPageImpl::m_nObjects.md)|Almacena el número de objetos asociado a la página de propiedades.|  
|[IPropertyPageImpl::m\_pPageSite](../Topic/IPropertyPageImpl::m_pPageSite.md)|Señala a la interfaz de `IPropertyPageSite` a través de la que la página de propiedades se comunica con el cuadro de la propiedad.|  
|[IPropertyPageImpl::m\_ppUnk](../Topic/IPropertyPageImpl::m_ppUnk.md)|Señala a una matriz de punteros de **IUnknown** a objetos asociado a la página de propiedades.|  
|[IPropertyPageImpl::m\_size](../Topic/IPropertyPageImpl::m_size.md)|Almacena el alto y el ancho del cuadro de diálogo página de propiedades, en píxeles.|  
  
## Comentarios  
 La interfaz de [IPropertyPage](http://msdn.microsoft.com/library/windows/desktop/ms691246) permite que un objeto administra una página de propiedades particular de una hoja de propiedades.  La clase `IPropertyPageImpl` proporciona una implementación predeterminada de esta interfaz y implementa **IUnknown** enviando información del dispositivo de volcado en versiones de depuración.  
  
 **artículos relacionados** [tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [Crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## Jerarquía de herencia  
 `IPropertyPage`  
  
 `IPropertyPageImpl`  
  
## Requisitos  
 **encabezado:** atlctl.h  
  
## Vea también  
 [IPropertyPage2Impl Class](../../atl/reference/ipropertypage2impl-class.md)   
 [IPerPropertyBrowsingImpl Class](../../atl/reference/iperpropertybrowsingimpl-class.md)   
 [ISpecifyPropertyPagesImpl Class](../../atl/reference/ispecifypropertypagesimpl-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)