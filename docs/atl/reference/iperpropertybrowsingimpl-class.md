---
title: "IPerPropertyBrowsingImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.IPerPropertyBrowsingImpl"
  - "IPerPropertyBrowsing"
  - "ATL::IPerPropertyBrowsingImpl"
  - "ATL::IPerPropertyBrowsingImpl<T>"
  - "IPerPropertyBrowsingImpl"
  - "ATL.IPerPropertyBrowsingImpl<T>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IPerPropertyBrowsing, implementación de ATL"
  - "IPerPropertyBrowsingImpl class"
  - "páginas de propiedades, accessing information"
ms.assetid: 0b1a9be3-d242-4767-be69-663a21e4b728
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# IPerPropertyBrowsingImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase implementa **IUnknown** y permite que el cliente tiene acceso a la información en las páginas de propiedades de un objeto.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## Sintaxis  
  
```  
  
      template<  
class T   
>  
class ATL_NO_VTABLE IPerPropertyBrowsingImpl :  
public IPerPropertyBrowsing  
```  
  
#### Parámetros  
 `T`  
 la clase, derivada de `IPerPropertyBrowsingImpl`.  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IPerPropertyBrowsingImpl::GetDisplayString](../Topic/IPerPropertyBrowsingImpl::GetDisplayString.md)|Recupera una cadena que describe una propiedad determinada.|  
|[IPerPropertyBrowsingImpl::GetPredefinedStrings](../Topic/IPerPropertyBrowsingImpl::GetPredefinedStrings.md)|Recupera una matriz de cadenas que corresponde a los valores que una propiedad determinada puede aceptar.|  
|[IPerPropertyBrowsingImpl::GetPredefinedValue](../Topic/IPerPropertyBrowsingImpl::GetPredefinedValue.md)|Recupera **VARIANT** que contiene el valor de una propiedad identificada por un DISPID especificado.  El identificador de envío es asociado al nombre de cadena recuperado de `GetPredefinedStrings`.  la implementación de ATL devuelve **E\_NOTIMPL**.|  
|[IPerPropertyBrowsingImpl::MapPropertyToPage](../Topic/IPerPropertyBrowsingImpl::MapPropertyToPage.md)|Recupera el CLSID de la página de propiedades asociada a una propiedad determinada.|  
  
## Comentarios  
 La interfaz de [IPerPropertyBrowsing](http://msdn.microsoft.com/library/windows/desktop/ms678432) permite que un cliente tiene acceso a la información en las páginas de propiedades de un objeto.  La clase `IPerPropertyBrowsingImpl` proporciona una implementación predeterminada de esta interfaz y implementa **IUnknown** enviando información del dispositivo de volcado en versiones de depuración.  
  
> [!NOTE]
>  Si utiliza Microsoft Access como la aplicación contenedora, debe derivar la clase de `IPerPropertyBrowsingImpl`.  Si no, Access no cargará el control.  
  
 **artículos relacionados** [tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [Crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## Jerarquía de herencia  
 `IPerPropertyBrowsing`  
  
 `IPerPropertyBrowsingImpl`  
  
## Requisitos  
 **encabezado:** atlctl.h  
  
## Vea también  
 [IPropertyPageImpl Class](../../atl/reference/ipropertypageimpl-class.md)   
 [ISpecifyPropertyPagesImpl Class](../../atl/reference/ispecifypropertypagesimpl-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)