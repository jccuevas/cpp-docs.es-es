---
title: "IOleControlImpl Class | Microsoft Docs"
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
  - "IOleControlImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IOleControlImpl class"
ms.assetid: 5a4255ad-ede4-49ca-ba9a-07c2e919fa85
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IOleControlImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona una implementación predeterminada de la interfaz de **IOleControl** e implementa **IUnknown**.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## Sintaxis  
  
```  
  
      template< class   
      T  
      >  
class IOleControlImpl  
```  
  
#### Parámetros  
 `T`  
 la clase, derivada de `IOleControlImpl`.  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IOleControlImpl::FreezeEvents](../Topic/IOleControlImpl::FreezeEvents.md)|Indica si el contenedor omite o aceptar eventos de control.|  
|[IOleControlImpl::GetControlInfo](../Topic/IOleControlImpl::GetControlInfo.md)|Toda la información sobre el comportamiento de teclado del control.  la implementación de ATL devuelve **E\_NOTIMPL**.|  
|[IOleControlImpl::OnAmbientPropertyChange](../Topic/IOleControlImpl::OnAmbientPropertyChange.md)|Informa a un control que uno o más de las propiedades de ambiente del contenedor han cambiado.  la implementación de ATL devuelve `S_OK`.|  
|[IOleControlImpl::OnMnemonic](../Topic/IOleControlImpl::OnMnemonic.md)|Informa al control que un usuario ha presionado una pulsación de tecla especificada.  la implementación de ATL devuelve **E\_NOTIMPL**.|  
  
## Comentarios  
 La clase `IOleControlImpl` proporciona una implementación predeterminada de la interfaz de [IOleControl](http://msdn.microsoft.com/library/windows/desktop/ms694320) e implementa **IUnknown** enviando información del dispositivo de volcado en compilaciones de depuración.  
  
 **artículos relacionados** [tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [Crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## Jerarquía de herencia  
 `IOleControl`  
  
 `IOleControlImpl`  
  
## Requisitos  
 **encabezado:** atlctl.h  
  
## Vea también  
 [IOleObjectImpl Class](../../atl/reference/ioleobjectimpl-class.md)   
 [ActiveX Controls Interfaces](http://msdn.microsoft.com/library/windows/desktop/ms692724)   
 [Class Overview](../../atl/atl-class-overview.md)