---
title: "CWindowImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CWindowImpl"
  - "ATL.CWindowImpl"
  - "CWindowImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWindowImpl class"
  - "subclassing windows, ATL"
ms.assetid: 02eefd45-a0a6-4d1b-99f6-dbf627e2cc2f
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CWindowImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona métodos para crear una ventana o subclases de una ventana.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## Sintaxis  
  
```  
  
      template <  
class T,  
class TBase= CWindow,  
class TWinTraits= CControlWinTraits   
>  
class ATL_NO_VTABLE CWindowImpl :  
public CWindowImplBaseT< TBase, TWinTraits>  
```  
  
#### Parámetros  
 `T`  
 Nueva clase derivada de `CWindowImpl`.  
  
 *TBase*  
 Clase base de la clase.  De manera predeterminada, la clase base es [CWindow](../../atl/reference/cwindow-class.md).  
  
 `TWinTraits`  
 [Clase de rasgos](../../atl/understanding-window-traits.md) que define los estilos de la ventana.  El valor predeterminado es `CControlWinTraits`.  
  
## Miembros  
  
### Métodos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CWindowImpl::Create](../Topic/CWindowImpl::Create.md)|Crea una ventana.|  
  
### Métodos de CWindowImplBaseT  
  
|||  
|-|-|  
|[DefWindowProc](../Topic/CWindowImpl::DefWindowProc.md)|Proporciona el procesamiento de mensajes predeterminado.|  
|[GetCurrentMessage](../Topic/CWindowImpl::GetCurrentMessage.md)|Devuelve el mensaje actual.|  
|[GetWindowProc](../Topic/CWindowImpl::GetWindowProc.md)|Devuelve el procedimiento de ventana actual.|  
|[OnFinalMessage](../Topic/CWindowImpl::OnFinalMessage.md)|Se llama después de recibir el último mensaje \(normalmente `WM_NCDESTROY`\).|  
|[SubclassWindow](../Topic/CWindowImpl::SubclassWindow.md)|Crea subclases de una ventana.|  
|[UnsubclassWindow](../Topic/CWindowImpl::UnsubclassWindow.md)|Restaura una ventana cuyas subclases se han creado previamente.|  
  
### Métodos estáticos  
  
|||  
|-|-|  
|[GetWndClassInfo](../Topic/CWindowImpl::GetWndClassInfo.md)|Devuelve una instancia estática de [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md), que administra la información de la clase de ventana.|  
|[WindowProc](../Topic/CWindowImpl::WindowProc.md)|Procesa los mensajes enviados a la ventana.|  
  
### Miembros de datos  
  
|||  
|-|-|  
|[m\_pfnSuperWindowProc](../Topic/CWindowImpl::m_pfnSuperWindowProc.md)|Señala al procedimiento de ventana original de la clase de la ventana.|  
  
## Comentarios  
 Puede utilizar `CWindowImpl` para crear una ventana o crear subclases de una ventana existente. El procedimiento de ventana `CWindowImpl` utiliza un mapa de mensajes para enviar los mensajes a los controladores adecuados.  
  
 `CWindowImpl::Create` crea una ventana basándose en la información de la clase de ventana que [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) administra.  `CWindowImpl` contiene la macro [DECLARE\_WND\_CLASS](../Topic/DECLARE_WND_CLASS.md), lo que significa que `CWndClassInfo` registra una nueva clase de ventana.  Si desea crear una superclase de una clase de ventana existente, derive la clase de `CWindowImpl` e incluya la macro [DECLARE\_WND\_SUPERCLASS](../Topic/DECLARE_WND_SUPERCLASS.md).  En este caso, `CWndClassInfo` registra una clase de ventana que se basa en una clase existente, pero utiliza `CWindowImpl::WindowProc`.  Por ejemplo:  
  
 [!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/CPP/cwindowimpl-class_1.h)]  
  
> [!NOTE]
>  Dado que `CWndClassInfo` administra la información solo para una clase de ventana, cada ventana creada con una instancia de `CWindowImpl` se basa en la misma clase de ventana.  
  
 `CWindowImpl` también permite crear subclases de una ventana.  El método `SubclassWindow` adjunta una ventana existente al objeto `CWindowImpl` y cambia el procedimiento de ventana a `CWindowImpl::WindowProc`.  Cada instancia de `CWindowImpl` puede crear subclases de una ventana diferente.  
  
> [!NOTE]
>  Para cualquier objeto `CWindowImpl` dado, llame a **Create** o `SubclassWindow`.  No invoque ambos métodos en el mismo objeto.  
  
 Además de `CWindowImpl`, ATL proporciona [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) para crear una ventana incluida en otro objeto.  
  
 El destructor de clase base \(~**CWindowImplRoot**\) garantiza que la ventana desaparezca antes de que se destruya el objeto.  
  
 `CWindowImpl` deriva de **CWindowImplBaseT**, que deriva de **CWindowImplRoot**, que deriva de **TBase** y de [CMessageMap](../../atl/reference/cmessagemap-class.md).  
  
|Para obtener más información sobre|Vea|  
|----------------------------------------|---------|  
|Crear controles|[Tutorial de ATL](../../atl/active-template-library-atl-tutorial.md)|  
|Utilizar ventanas en ATL|[Clases de ventana ATL](../../atl/atl-window-classes.md)|  
|Asistente para proyectos ATL|[Crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)|  
  
## Jerarquía de herencia  
 [CMessageMap](../../atl/reference/cmessagemap-class.md)  
  
 `TBase`  
  
 `CWindowImplRoot`  
  
 `CWindowImplBaseT`  
  
 `CWindowImpl`  
  
## Requisitos  
 **Encabezado:** atlwin.h  
  
## Vea también  
 [BEGIN\_MSG\_MAP](../Topic/BEGIN_MSG_MAP.md)   
 [CComControl Class](../../atl/reference/ccomcontrol-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)