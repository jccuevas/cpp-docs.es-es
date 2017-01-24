---
title: "IOleObjectImpl Class | Microsoft Docs"
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
  - "ATL.IOleObjectImpl"
  - "ATL.IOleObjectImpl<T>"
  - "ATL::IOleObjectImpl"
  - "ATL::IOleObjectImpl<T>"
  - "IOleObjectImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controles ActiveX [C++], communication between container and control"
  - "IOleObject, implementación de ATL"
  - "IOleObjectImpl class"
ms.assetid: 59750b2d-1633-4a51-a4c2-6455b6b90c45
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IOleObjectImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase implementa **IUnknown** y es la interfaz principal a través de la cual un contenedor se comunica con un control.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## Sintaxis  
  
```  
  
      template<  
class T   
>  
class ATL_NO_VTABLE IOleObjectImpl :  
public IOleObject  
```  
  
#### Parámetros  
 `T`  
 la clase, derivada de `IOleObjectImpl`.  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IOleObjectImpl::Advise](../Topic/IOleObjectImpl::Advise.md)|Establece una conexión asesor con el control.|  
|[IOleObjectImpl::Close](../Topic/IOleObjectImpl::Close.md)|Cambia el estado de control de ejecución a cargado.|  
|[IOleObjectImpl::DoVerb](../Topic/IOleObjectImpl::DoVerb.md)|Indica al control que realice una de las acciones enumeradas.|  
|[IOleObjectImpl::DoVerbDiscardUndo](../Topic/IOleObjectImpl::DoVerbDiscardUndo.md)|Indica al control que descarte cualquier estado de deshacer que está manteniendo.|  
|[IOleObjectImpl::DoVerbHide](../Topic/IOleObjectImpl::DoVerbHide.md)|Indica al control que quite su interfaz de usuario de la vista.|  
|[IOleObjectImpl::DoVerbInPlaceActivate](../Topic/IOleObjectImpl::DoVerbInPlaceActivate.md)|Ejecuta el control e instala la ventana, pero no instala la interfaz de usuario del control.|  
|[IOleObjectImpl::DoVerbOpen](../Topic/IOleObjectImpl::DoVerbOpen.md)|Hace que el control Abrir\-que se editan en una ventana independiente.|  
|[IOleObjectImpl::DoVerbPrimary](../Topic/IOleObjectImpl::DoVerbPrimary.md)|Realiza la acción especificada cuando el usuario hace doble clic en el control.  El control define la acción, para activar normalmente el control en contexto.|  
|[IOleObjectImpl::DoVerbShow](../Topic/IOleObjectImpl::DoVerbShow.md)|Se muestra un control insertado recientemente al usuario.|  
|[IOleObjectImpl::DoVerbUIActivate](../Topic/IOleObjectImpl::DoVerbUIActivate.md)|Activa el control en contexto y muestra la interfaz de usuario del control, como menús y barras de herramientas.|  
|[IOleObjectImpl::EnumAdvise](../Topic/IOleObjectImpl::EnumAdvise.md)|Muestra las conexiones asesores del control.|  
|[IOleObjectImpl::EnumVerbs](../Topic/IOleObjectImpl::EnumVerbs.md)|Muestra las acciones para el control.|  
|[IOleObjectImpl::GetClientSite](../Topic/IOleObjectImpl::GetClientSite.md)|Recupera el sitio del control.|  
|[IOleObjectImpl::GetClipboardData](../Topic/IOleObjectImpl::GetClipboardData.md)|Recupera datos del portapapeles.  la implementación de ATL devuelve **E\_NOTIMPL**.|  
|[IOleObjectImpl::GetExtent](../Topic/IOleObjectImpl::GetExtent.md)|Recupera la extensión de presentación del control.|  
|[IOleObjectImpl::GetMiscStatus](../Topic/IOleObjectImpl::GetMiscStatus.md)|Recupera el estado de control.|  
|[IOleObjectImpl::GetMoniker](../Topic/IOleObjectImpl::GetMoniker.md)|Recupera el moniker del control.  la implementación de ATL devuelve **E\_NOTIMPL**.|  
|[IOleObjectImpl::GetUserClassID](../Topic/IOleObjectImpl::GetUserClassID.md)|Recupera el identificador de clase del control.|  
|[IOleObjectImpl::GetUserType](../Topic/IOleObjectImpl::GetUserType.md)|Recupera el nombre de usuario\- tipo de control.|  
|[IOleObjectImpl::InitFromData](../Topic/IOleObjectImpl::InitFromData.md)|Inicializa el control de datos seleccionado.  la implementación de ATL devuelve **E\_NOTIMPL**.|  
|[IOleObjectImpl::IsUpToDate](../Topic/IOleObjectImpl::IsUpToDate.md)|Comprueba si el control está actualizado.  la implementación de ATL devuelve `S_OK`.|  
|[IOleObjectImpl::OnPostVerbDiscardUndo](../Topic/IOleObjectImpl::OnPostVerbDiscardUndo.md)|Llamado por [DoVerbDiscardUndo](../Topic/IOleObjectImpl::DoVerbDiscardUndo.md) después del estado de deshacer se descarta.|  
|[IOleObjectImpl::OnPostVerbHide](../Topic/IOleObjectImpl::OnPostVerbHide.md)|Llamado por [DoVerbHide](../Topic/IOleObjectImpl::DoVerbHide.md) después del control está oculto.|  
|[IOleObjectImpl::OnPostVerbInPlaceActivate](../Topic/IOleObjectImpl::OnPostVerbInPlaceActivate.md)|Llamado por [DoVerbInPlaceActivate](../Topic/IOleObjectImpl::DoVerbInPlaceActivate.md) después del control se provoca en contexto.|  
|[IOleObjectImpl::OnPostVerbOpen](../Topic/IOleObjectImpl::OnPostVerbOpen.md)|Llamado por [DoVerbOpen](../Topic/IOleObjectImpl::DoVerbOpen.md) después de que el control se haya abierto para edición en una ventana independiente.|  
|[IOleObjectImpl::OnPostVerbShow](../Topic/IOleObjectImpl::OnPostVerbShow.md)|Llamado por [DoVerbShow](../Topic/IOleObjectImpl::DoVerbShow.md) después de que el control se ha creado visible.|  
|[IOleObjectImpl::OnPostVerbUIActivate](../Topic/IOleObjectImpl::OnPostVerbUIActivate.md)|Llamado por [DoVerbUIActivate](../Topic/IOleObjectImpl::DoVerbUIActivate.md) después de que se ha desencadenado la interfaz de usuario del control.|  
|[IOleObjectImpl::OnPreVerbDiscardUndo](../Topic/IOleObjectImpl::OnPreVerbDiscardUndo.md)|Llamado por [DoVerbDiscardUndo](../Topic/IOleObjectImpl::DoVerbDiscardUndo.md) antes del estado de deshacer se descarta.|  
|[IOleObjectImpl::OnPreVerbHide](../Topic/IOleObjectImpl::OnPreVerbHide.md)|Llamado por [DoVerbHide](../Topic/IOleObjectImpl::DoVerbHide.md) antes del control está oculto.|  
|[IOleObjectImpl::OnPreVerbInPlaceActivate](../Topic/IOleObjectImpl::OnPreVerbInPlaceActivate.md)|Llamado por [DoVerbInPlaceActivate](../Topic/IOleObjectImpl::DoVerbInPlaceActivate.md) antes del control se provoca en contexto.|  
|[IOleObjectImpl::OnPreVerbOpen](../Topic/IOleObjectImpl::OnPreVerbOpen.md)|Llamado por [DoVerbOpen](../Topic/IOleObjectImpl::DoVerbOpen.md) antes de que el control se haya abierto para edición en una ventana independiente.|  
|[IOleObjectImpl::OnPreVerbShow](../Topic/IOleObjectImpl::OnPreVerbShow.md)|Llamado por [DoVerbShow](../Topic/IOleObjectImpl::DoVerbShow.md) antes de que el control se ha creado visible.|  
|[IOleObjectImpl::OnPreVerbUIActivate](../Topic/IOleObjectImpl::OnPreVerbUIActivate.md)|Llamado por [DoVerbUIActivate](../Topic/IOleObjectImpl::DoVerbUIActivate.md) antes de que se ha desencadenado la interfaz de usuario del control.|  
|[IOleObjectImpl::SetClientSite](../Topic/IOleObjectImpl::SetClientSite.md)|Informa al control del sitio de cliente en el contenedor.|  
|[IOleObjectImpl::SetColorScheme](../Topic/IOleObjectImpl::SetColorScheme.md)|Recomienda una combinación de colores a la aplicación del control, si la hay.  la implementación de ATL devuelve **E\_NOTIMPL**.|  
|[IOleObjectImpl::SetExtent](../Topic/IOleObjectImpl::SetExtent.md)|Establece la extensión de presentación del control.|  
|[IOleObjectImpl::SetHostNames](../Topic/IOleObjectImpl::SetHostNames.md)|Indica al control los nombres de la aplicación contenedora y el documento contenedor.|  
|[IOleObjectImpl::SetMoniker](../Topic/IOleObjectImpl::SetMoniker.md)|Indica al control cuál es el moniker.  la implementación de ATL devuelve **E\_NOTIMPL**.|  
|[IOleObjectImpl::Unadvise](../Topic/IOleObjectImpl::Unadvise.md)|Elimina una conexión asesor con el control.|  
|[IOleObjectImpl::Update](../Topic/IOleObjectImpl::Update.md)|actualiza el control.  la implementación de ATL devuelve `S_OK`.|  
  
## Comentarios  
 La interfaz de [IOleObject](http://msdn.microsoft.com/library/windows/desktop/dd542709) es la interfaz de la entidad de seguridad a través de la cual un contenedor se comunica con un control.  La clase `IOleObjectImpl` proporciona una implementación predeterminada de esta interfaz y implementa **IUnknown** enviando información del dispositivo de volcado en versiones de depuración.  
  
 **artículos relacionados** [tutorial de ATL](../../atl/active-template-library-atl-tutorial.md), [Crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)  
  
## Jerarquía de herencia  
 `IOleObject`  
  
 `IOleObjectImpl`  
  
## Requisitos  
 **encabezado:** atlctl.h  
  
## Vea también  
 [CComControl Class](../../atl/reference/ccomcontrol-class.md)   
 [ActiveX Controls Interfaces](http://msdn.microsoft.com/library/windows/desktop/ms692724)   
 [Class Overview](../../atl/atl-class-overview.md)