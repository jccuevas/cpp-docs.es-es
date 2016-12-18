---
title: "ISpecifyPropertyPagesImpl Class | Microsoft Docs"
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
  - "ISpecifyPropertyPagesImpl"
  - "ATL.ISpecifyPropertyPagesImpl<T>"
  - "ATL::ISpecifyPropertyPagesImpl"
  - "ATL::ISpecifyPropertyPagesImpl<T>"
  - "ATL.ISpecifyPropertyPagesImpl"
  - "ISpecifyPropertyPagesImpl Class"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ISpecifyPropertyPages"
  - "ISpecifyPropertyPagesImpl class"
  - "páginas de propiedades, CLSIDs associated with"
ms.assetid: 4e4b9795-b656-4d56-9b8c-85941e7731f9
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ISpecifyPropertyPagesImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

esta clase implementa **IUnknown** y proporciona una implementación predeterminada de la interfaz de [ISpecifyPropertyPages](http://msdn.microsoft.com/library/windows/desktop/ms695217) .  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## Sintaxis  
  
```  
  
      template<  
class T   
>  
class ATL_NO_VTABLE ISpecifyPropertyPagesImpl :  
public ISpecifyPropertyPages  
```  
  
#### Parámetros  
 `T`  
 la clase, derivada de `ISpecifyPropertyPagesImpl`.  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ISpecifyPropertyPagesImpl::GetPages](../Topic/ISpecifyPropertyPagesImpl::GetPages.md)|Rellena una matriz contado de valores de identificador UUID.  Cada identificador UUID corresponde al CLSID para una de las páginas de propiedades que se pueden mostrar en la hoja de propiedades del objeto.|  
  
## Comentarios  
 La interfaz de [ISpecifyPropertyPages](http://msdn.microsoft.com/library/windows/desktop/ms695217) permite a un cliente para obtener una lista de CLSID para las páginas de propiedades admitidas por un objeto.  La clase `ISpecifyPropertyPagesImpl` proporciona una implementación predeterminada de esta interfaz y implementa **IUnknown** enviando información del dispositivo de volcado en versiones de depuración.  
  
> [!NOTE]
>  No exponga la interfaz de **ISpecifyPropertyPages** si el objeto no admite las páginas de propiedades.  
  
 **artículos relacionados** [tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [Crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## Jerarquía de herencia  
 `ISpecifyPropertyPages`  
  
 `ISpecifyPropertyPagesImpl`  
  
## Requisitos  
 **encabezado:** atlcom.h  
  
## Vea también  
 [IPropertyPageImpl Class](../../atl/reference/ipropertypageimpl-class.md)   
 [IPerPropertyBrowsingImpl Class](../../atl/reference/iperpropertybrowsingimpl-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)