---
title: "IOleInPlaceActiveObjectImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IOleInPlaceActiveObjectImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controles ActiveX [C++], communication between container and control"
  - "IOleInPlaceActiveObject, implementación de ATL"
  - "IOleInPlaceActiveObjectImpl class"
ms.assetid: 44e6cc6d-a2dc-4187-98e3-73cf0320dea9
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# IOleInPlaceActiveObjectImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos para ayudar a la comunicación entre un control en contexto y su contenedor.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## Sintaxis  
  
```  
  
      template< class   
      T  
      >  
class IOleInPlaceActiveObjectImpl  
```  
  
#### Parámetros  
 `T`  
 la clase, derivada de `IOleInPlaceActiveObjectImpl`.  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IOleInPlaceActiveObjectImpl::ContextSensitiveHelp](../Topic/IOleInPlaceActiveObjectImpl::ContextSensitiveHelp.md)|Habilita ayuda contextual.  la implementación de ATL devuelve **E\_NOTIMPL**.|  
|[IOleInPlaceActiveObjectImpl::EnableModeless](../Topic/IOleInPlaceActiveObjectImpl::EnableModeless.md)|Habilita los cuadros de diálogo no modal.  la implementación de ATL devuelve `S_OK`.|  
|[IOleInPlaceActiveObjectImpl::GetWindow](../Topic/IOleInPlaceActiveObjectImpl::GetWindow.md)|Obtiene un identificador de ventana.|  
|[IOleInPlaceActiveObjectImpl::OnDocWindowActivate](../Topic/IOleInPlaceActiveObjectImpl::OnDocWindowActivate.md)|Notifica al control cuando se activa o desactiva la ventana de documento del contenedor.  la implementación de ATL devuelve `S_OK`.|  
|[IOleInPlaceActiveObjectImpl::OnFrameWindowActivate](../Topic/IOleInPlaceActiveObjectImpl::OnFrameWindowActivate.md)|Notifica al control cuando se activa o desactiva la ventana de nivel superior del cuadro del contenedor.  Retornos de implementación ATL|  
|[IOleInPlaceActiveObjectImpl::ResizeBorder](../Topic/IOleInPlaceActiveObjectImpl::ResizeBorder.md)|Informa al control que necesite cambiar el tamaño de sus bordes.  la implementación de ATL devuelve `S_OK`.|  
|[IOleInPlaceActiveObjectImpl::TranslateAccelerator](../Topic/IOleInPlaceActiveObjectImpl::TranslateAccelerator.md)|Procesa los mensajes de la tecla de aceleración del menú del contenedor.  la implementación de ATL devuelve **E\_NOTIMPL**.|  
  
## Comentarios  
 La interfaz de [IOleInPlaceActiveObject](http://msdn.microsoft.com/library/windows/desktop/ms691299) ayuda a la comunicación entre un control en contexto y su contenedor; por ejemplo, comunicándose al estado activo del control y el contenedor, e informando el control necesita volverse el tamaño.  La clase `IOleInPlaceActiveObjectImpl` proporciona una implementación predeterminada de `IOleInPlaceActiveObject` y admite **IUnknown** enviando información del dispositivo de volcado en compilaciones de depuración.  
  
 **artículos relacionados** [tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [Crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## Jerarquía de herencia  
 `IOleInPlaceActiveObject`  
  
 `IOleInPlaceActiveObjectImpl`  
  
## Requisitos  
 **encabezado:** atlctl.h  
  
## Vea también  
 [CComControl Class](../../atl/reference/ccomcontrol-class.md)   
 [ActiveX Controls Interfaces](http://msdn.microsoft.com/library/windows/desktop/ms692724)   
 [Class Overview](../../atl/atl-class-overview.md)