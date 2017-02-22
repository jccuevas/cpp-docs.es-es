---
title: "IOleInPlaceObjectWindowlessImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IOleInPlaceObjectWindowlessImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "activation [C++], ATL"
  - "controles ActiveX [C++], communication between container and control"
  - "controles [ATL], windowless"
  - "deactivating ATL"
  - "IOleInPlaceObjectWindowless, implementación de ATL"
  - "IOleInPlaceObjectWindowlessImpl class"
ms.assetid: a2e0feb4-bc59-4adf-aab2-105457bbdbb4
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# IOleInPlaceObjectWindowlessImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase implementa **IUnknown** y proporciona métodos que permiten a un control sin ventana para recibir mensajes de la ventana y para participar en operaciones de arrastrar y colocar.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## Sintaxis  
  
```  
  
      template< class   
      T  
      >  
class IOleInPlaceObjectWindowlessImpl  
```  
  
#### Parámetros  
 `T`  
 la clase, derivada de `IOleInPlaceObjectWindowlessImpl`.  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp](../Topic/IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp.md)|Habilita ayuda contextual.  la implementación de ATL devuelve **E\_NOTIMPL**.|  
|[IOleInPlaceObjectWindowlessImpl::GetDropTarget](../Topic/IOleInPlaceObjectWindowlessImpl::GetDropTarget.md)|Proporciona la interfaz de `IDropTarget` para un activo en contexto, objeto sin ventana que admite arrastrar y colocar.  la implementación de ATL devuelve **E\_NOTIMPL**.|  
|[IOleInPlaceObjectWindowlessImpl::GetWindow](../Topic/IOleInPlaceObjectWindowlessImpl::GetWindow.md)|Obtiene un identificador de ventana.|  
|[IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate](../Topic/IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate.md)|desactiva un control en contexto activo.|  
|[IOleInPlaceObjectWindowlessImpl::OnWindowMessage](../Topic/IOleInPlaceObjectWindowlessImpl::OnWindowMessage.md)|Envía un mensaje del contenedor a un control sin ventana que está activa en contexto.|  
|[IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo](../Topic/IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo.md)|Reactivar un control previamente unchecked.  la implementación de ATL devuelve **E\_NOTIMPL**.|  
|[IOleInPlaceObjectWindowlessImpl::SetObjectRects](../Topic/IOleInPlaceObjectWindowlessImpl::SetObjectRects.md)|Indica qué parte del control en contexto está visible.|  
|[IOleInPlaceObjectWindowlessImpl::UIDeactivate](../Topic/IOleInPlaceObjectWindowlessImpl::UIDeactivate.md)|desactiva y quita la interfaz de usuario que admite la activación en contexto.|  
  
## Comentarios  
 La interfaz de [IOleInPlaceObject](http://msdn.microsoft.com/library/windows/desktop/ms692646) administra la reactivación y la desactivación de controles en contexto y determina cuánto de control debe ser visible.  La interfaz de [IOleInPlaceObjectWindowless](http://msdn.microsoft.com/library/windows/desktop/ms687304) permite a un control sin ventana para recibir mensajes de la ventana y para participar en operaciones de arrastrar y colocar.  La clase `IOleInPlaceObjectWindowlessImpl` proporciona una implementación predeterminada de `IOleInPlaceObject` y de `IOleInPlaceObjectWindowless` e implementa **IUnknown** enviando información del dispositivo de volcado en versiones de depuración.  
  
 **artículos relacionados** [tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [Crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## Jerarquía de herencia  
 `IOleInPlaceObjectWindowless`  
  
 `IOleInPlaceObjectWindowlessImpl`  
  
## Requisitos  
 **encabezado:** atlctl.h  
  
## Vea también  
 [CComControl Class](../../atl/reference/ccomcontrol-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)