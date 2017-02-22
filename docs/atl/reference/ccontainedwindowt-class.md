---
title: "CContainedWindowT Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CContainedWindow"
  - "CContainedWindowT"
  - "ATL.CContainedWindowT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CContainedWindow class"
  - "CContainedWindowT class"
  - "contained windows"
ms.assetid: cde0ca36-9347-4068-995a-d294dae57ca9
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CContainedWindowT Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

esta clase implementa una ventana contenida dentro de otro objeto.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
      template <  
class TBase= CWindow,  
class TWinTraits= CControlWinTraits   
>  
class CContainedWindowT :  
public TBase  
```  
  
#### Parámetros  
 *TBase*  
 la clase base de la nueva clase.  la clase base predeterminada es `CWindow`.  
  
 `TWinTraits`  
 Una clase de con los que define los estilos de la ventana.  El valor predeterminado es `CControlWinTraits`.  
  
> [!NOTE]
>  [CContainedWindow](../Topic/CContainedWindow.md) es una especialización de `CContainedWindowT`.  Si desea cambiar la clase base o los rasgos, utilice `CContainedWindowT` directamente.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CContainedWindowT::CContainedWindowT](../Topic/CContainedWindowT::CContainedWindowT.md)|Constructor.  Se inicializan los miembros de datos para especificar que el mapa de mensajes procesará los mensajes de la ventana contenida.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CContainedWindowT::Create](../Topic/CContainedWindowT::Create.md)|crea una ventana.|  
|[CContainedWindowT::DefWindowProc](../Topic/CContainedWindowT::DefWindowProc.md)|Proporciona el procesamiento de mensajes predeterminado.|  
|[CContainedWindowT::GetCurrentMessage](../Topic/CContainedWindowT::GetCurrentMessage.md)|devuelve el mensaje actual.|  
|[CContainedWindowT::RegisterWndSuperclass](../Topic/CContainedWindowT::RegisterWndSuperclass.md)|Registra la clase de ventana contenida.|  
|[CContainedWindowT::SubclassWindow](../Topic/CContainedWindowT::SubclassWindow.md)|Crea una subclase de una ventana.|  
|[CContainedWindowT::SwitchMessageMap](../Topic/CContainedWindowT::SwitchMessageMap.md)|Cambia al mapa de mensajes se utiliza para procesar los mensajes de la ventana contenida.|  
|[CContainedWindowT::UnsubclassWindow](../Topic/CContainedWindowT::UnsubclassWindow.md)|Restaura una ventana previamente subclases.|  
|[CContainedWindowT::WindowProc](../Topic/CContainedWindowT::WindowProc.md)|\(Estático\) procesa los mensajes enviados a la ventana contenida.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CContainedWindowT::m\_dwMsgMapID](../Topic/CContainedWindowT::m_dwMsgMapID.md)|Identifica que el mapa de mensajes procesará los mensajes de la ventana contenida.|  
|[CContainedWindowT::m\_lpszClassName](../Topic/CContainedWindowT::m_lpszClassName.md)|Especifica el nombre de una clase de ventana existente en la que una nueva clase de ventana está basada en.|  
|[CContainedWindowT::m\_pfnSuperWindowProc](../Topic/CContainedWindowT::m_pfnSuperWindowProc.md)|Señala al procedimiento de ventana original de la clase de la ventana.|  
|[CContainedWindowT::m\_pObject](../Topic/CContainedWindowT::m_pObject.md)|Señala al objeto que contiene.|  
  
## Comentarios  
 `CContainedWindowT` implementa una ventana contenida dentro de otro objeto.  el procedimiento de ventana de los entity\_CContainedWindowT utiliza un mapa de mensajes en el objeto que contiene los mensajes directos controladores adecuados.  Al crear un objeto de `CContainedWindowT` , especifica que el mapa de mensajes se debe utilizar.  
  
 `CContainedWindowT` permite crear una nueva ventana creando utiliza una clase de ventana existente.  el método de **Crear** primero registra una clase de ventana que se base en una clase existente pero utiliza `CContainedWindowT::WindowProc`.  **Crear** crea una ventana basada en esta nueva clase de ventana.  Cada instancia de `CContainedWindowT` puede crear superclase otra clase de ventana.  
  
 `CContainedWindowT` también permite crear subclases de la ventana.  El método de `SubclassWindow` adjunta una ventana existente al objeto de `CContainedWindowT` y cambia el procedimiento de ventana para `CContainedWindowT::WindowProc`.  Cada instancia de `CContainedWindowT` puede crear subclases de una ventana diferente.  
  
> [!NOTE]
>  Para cualquier objeto determinado de `CContainedWindowT` , llame a **Crear** o `SubclassWindow`.  No debe invocar ambos métodos en el mismo objeto.  
  
 Al utilizar la opción **Agregue el control basado en** en el asistente para proyectos ATL, el asistente automáticamente agregará un miembro de datos de `CContainedWindowT` a la clase que implementa el control.  El ejemplo siguiente se muestra cómo se declara la ventana contenida:  
  
 [!code-cpp[NVC_ATL_Windowing#38](../../atl/codesnippet/CPP/ccontainedwindowt-class_1.h)]  
  
 [!code-cpp[NVC_ATL_Windowing#39](../../atl/codesnippet/CPP/ccontainedwindowt-class_2.h)]  
  
 [!code-cpp[NVC_ATL_Windowing#40](../../atl/codesnippet/CPP/ccontainedwindowt-class_3.h)]  
  
|Para obtener más información sobre|Vea|  
|----------------------------------------|---------|  
|Crear controles|[tutorial de ATL](../../atl/active-template-library-atl-tutorial.md)|  
|Utilizando las ventanas en ATL|[Clases de ventana ATL](../../atl/atl-window-classes.md)|  
|Asistente para proyectos ATL|[Crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md)|  
|Ventanas|[Ventanas](http://msdn.microsoft.com/library/windows/desktop/ms632595) y los temas siguientes en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]|  
  
## Jerarquía de herencia  
 `TBase`  
  
 `CContainedWindowT`  
  
## Requisitos  
 **encabezado:** atlwin.h  
  
## Vea también  
 [CWindow Class](../../atl/reference/cwindow-class.md)   
 [CWindowImpl Class](../../atl/reference/cwindowimpl-class.md)   
 [CMessageMap Class](../../atl/reference/cmessagemap-class.md)   
 [BEGIN\_MSG\_MAP](../Topic/BEGIN_MSG_MAP.md)   
 [ALT\_MSG\_MAP](../Topic/ALT_MSG_MAP.md)   
 [Class Overview](../../atl/atl-class-overview.md)