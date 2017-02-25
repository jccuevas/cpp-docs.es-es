---
title: "CComControl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CComControl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ambient properties"
  - "CComControl class"
  - "CComControlBase class, CComControl class"
  - "control flags"
  - "controles [ATL], control helper functions"
  - "controles [ATL], propiedades"
  - "propiedades estándar, ATL"
ms.assetid: 55368c27-bd16-45a7-b701-edb36157c8e8
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CComControl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos para crear y administrar controles ATL.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
      template <  
class T,  
class WinBase= CWindowImpl< T>   
>  
class ATL_NO_VTABLE CComControl :  
public CComControlBase, public WinBase;  
```  
  
#### Parámetros  
 `T`  
 La clase que implementa el control.  
  
 *WinBase*  
 La clase base que implementa funciones de visualización en una ventana.  Valores predeterminados a [CWindowImpl](../../atl/reference/cwindowimpl-class.md).  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComControl::CComControl](../Topic/CComControl::CComControl.md)|Constructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComControl::ControlQueryInterface](../Topic/CComControl::ControlQueryInterface.md)|recupera un puntero a la interfaz solicitada.|  
|[CComControl::CreateControlWindow](../Topic/CComControl::CreateControlWindow.md)|Crea una ventana para el control.|  
|[CComControl::FireOnChanged](../Topic/CComControl::FireOnChanged.md)|Notifica al receptor de contenedor que una propiedad de control ha cambiado.|  
|[CComControl::FireOnRequestEdit](../Topic/CComControl::FireOnRequestEdit.md)|Notifica al receptor de contenedor que una propiedad de control está a punto de cambiar y que el objeto sea pide al receptor cómo continuar.|  
|[CComControl::MessageBox](../Topic/CComControl::MessageBox.md)|Llame a este método para crear, para mostrar, y para operar un cuadro de mensaje.|  
  
## Comentarios  
 `CComControl` es un conjunto de funciones útiles auxiliares de control y miembros de datos esenciales para controles ATL.  Cuando crea un control estándar o un control DHTML mediante el asistente para controles ATL, el asistente automáticamente derivará la clase de `CComControl`.  `CComControl` derivan la mayoría de los métodos de [CComControlBase](../../atl/reference/ccomcontrolbase-class.md).  
  
 Para obtener más información sobre cómo crear un control, vea [tutorial de ATL](../../atl/active-template-library-atl-tutorial.md).  Para obtener más información sobre el asistente para proyectos ATL, vea el artículo [Crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md).  
  
 Para obtener una descripción de los métodos y miembros de datos de `CComControl` , vea el ejemplo de [CIRC](../../top/visual-cpp-samples.md) .  
  
## Jerarquía de herencia  
 `WinBase`  
  
 [CComControlBase](../../atl/reference/ccomcontrolbase-class.md)  
  
 `CComControl`  
  
## Requisitos  
 **encabezado:** atlctl.h  
  
## Vea también  
 [CWindowImpl Class](../../atl/reference/cwindowimpl-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [CComControlBase Class](../../atl/reference/ccomcontrolbase-class.md)   
 [CComCompositeControl Class](../../atl/reference/ccomcompositecontrol-class.md)