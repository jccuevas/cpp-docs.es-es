---
title: "IViewObjectExImpl Class | Microsoft Docs"
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
  - "ATL::IViewObjectExImpl<T>"
  - "ATL.IViewObjectExImpl"
  - "ATL::IViewObjectExImpl"
  - "ATL.IViewObjectExImpl<T>"
  - "IViewObjectExImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controles ActiveX [C++], dibujar"
  - "advise sinks"
  - "IViewObjectEx ATL implementation"
  - "IViewObjectExImpl class"
ms.assetid: ad6de760-1ee5-4883-b033-ae57beffc369
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IViewObjectExImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase implementa **IUnknown** y proporciona implementaciones predeterminadas de las interfaces de [IViewObject](http://msdn.microsoft.com/library/windows/desktop/ms680763), de [IViewObject2](http://msdn.microsoft.com/library/windows/desktop/ms691318), y de [IViewObjectEx](http://msdn.microsoft.com/library/windows/desktop/ms682375) .  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## Sintaxis  
  
```  
  
      template<  
class T   
>  
class ATL_NO_VTABLE IViewObjectExImpl :  
public IViewObjectEx  
```  
  
#### Parámetros  
 `T`  
 la clase, derivada de `IViewObjectExImpl`.  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IViewObjectExImpl::Draw](../Topic/IViewObjectExImpl::Draw.md)|Dibuja una representación del control sobre un contexto de dispositivo.|  
|[IViewObjectExImpl::Freeze](../Topic/IViewObjectExImpl::Freeze.md)|Inmovilizar la representación dibujada de un control para que no cambiará hasta `Unfreeze`.  la implementación de ATL devuelve **E\_NOTIMPL**.|  
|[IViewObjectExImpl::GetAdvise](../Topic/IViewObjectExImpl::GetAdvise.md)|Recupera una conexión asesor existente del receptor del control, si hay alguno.|  
|[IViewObjectExImpl::GetColorSet](../Topic/IViewObjectExImpl::GetColorSet.md)|Devuelve la paleta lógica utilizada por el control para dibujar.  la implementación de ATL devuelve **E\_NOTIMPL**.|  
|[IViewObjectExImpl::GetExtent](../Topic/IViewObjectExImpl::GetExtent.md)|Recupera el tamaño de presentación del control en unidades de HIMETRIC \(0,01 milímetros por unidad\) del miembro de datos [CComControlBase:: m\_sizeExtent](../Topic/CComControlBase::m_sizeExtent.md)de la clase de control.|  
|[IViewObjectExImpl::GetNaturalExtent](../Topic/IViewObjectExImpl::GetNaturalExtent.md)|Proporciona sugerencias de tamaño del contenedor del objeto para utilizarla como el usuario se cambia su tamaño.|  
|[IViewObjectExImpl::GetRect](../Topic/IViewObjectExImpl::GetRect.md)|Devuelve un rectángulo que describe un aspecto de dibujo solicitado.  la implementación de ATL devuelve **E\_NOTIMPL**.|  
|[IViewObjectExImpl::GetViewStatus](../Topic/IViewObjectExImpl::GetViewStatus.md)|Devuelve información sobre la opacidad del objeto y se admiten qué aspectos del gráfico.|  
|[IViewObjectExImpl::QueryHitPoint](../Topic/IViewObjectExImpl::QueryHitPoint.md)|Comprueba si el punto especificado está en el rectángulo especificado y devuelve un valor de [HITRESULT](http://msdn.microsoft.com/library/windows/desktop/ms682187) en `pHitResult`.|  
|[IViewObjectExImpl::QueryHitRect](../Topic/IViewObjectExImpl::QueryHitRect.md)|Comprueba si el rectángulo de presentación del control se superpone cualquier punto del rectángulo especificado location y devuelve un valor de **HITRESULT** en `pHitResult`.|  
|[IViewObjectExImpl::SetAdvise](../Topic/IViewObjectExImpl::SetAdvise.md)|Establece una conexión entre el control y un receptor advise por lo que el receptor puede recibir una notificación sobre cambios en la vista de control.|  
|[IViewObjectExImpl::Unfreeze](../Topic/IViewObjectExImpl::Unfreeze.md)|Libera la representación dibujada del control.  la implementación de ATL devuelve **E\_NOTIMPL**.|  
  
## Comentarios  
 Las interfaces de [IViewObject](http://msdn.microsoft.com/library/windows/desktop/ms680763), de [IViewObject2](http://msdn.microsoft.com/library/windows/desktop/ms691318), y de [IViewObjectEx](http://msdn.microsoft.com/library/windows/desktop/ms682375) permiten un control para mostrarse directamente, y crear y administrar un receptor advise para notificar al contenedor de cambios en que el control muestre.  La interfaz de **IViewObjectEx** proporciona compatibilidad con las características extendidas de control como gráfico libre de centelleo, los controles no rectangulares y transparentes, y prueba de posicionamiento \(por ejemplo, la proximidad de un clic del mouse debe deber considerarse en el control\).  La clase `IViewObjectExImpl` proporciona una implementación predeterminada de estas interfaces e implementa **IUnknown** enviando información del dispositivo de volcado en versiones de depuración.  
  
## Jerarquía de herencia  
 `IViewObjectEx`  
  
 `IViewObjectExImpl`  
  
## Requisitos  
 **encabezado:** atlctl.h  
  
## Vea también  
 [CComControl Class](../../atl/reference/ccomcontrol-class.md)   
 [ActiveX Controls Interfaces](http://msdn.microsoft.com/library/windows/desktop/ms692724)   
 [Tutorial](../../atl/active-template-library-atl-tutorial.md)   
 [Crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)   
 [Class Overview](../../atl/atl-class-overview.md)