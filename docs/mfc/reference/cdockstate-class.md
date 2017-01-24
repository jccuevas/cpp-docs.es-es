---
title: "CDockState Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDockState"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDockState class"
  - "dock state"
  - "docking control bars"
  - "docking tool windows"
  - "posición, control bar"
  - "tamaño"
  - "tamaño, control bar"
  - "estados, dockable control bar"
ms.assetid: 09e7c10b-3abd-4cb2-ad36-42420fe6bc36
caps.latest.revision: 23
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDockState Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una clase serializada de `CObject` que carga, descarga, o desactive el estado de una o más barras de control de acoplamiento en memoria persistente \(un archivo\).  
  
## Sintaxis  
  
```  
class CDockState : public CObject  
```  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDockState::Clear](../Topic/CDockState::Clear.md)|Borra la información de estado de vinculación.|  
|[CDockState::GetVersion](../Topic/CDockState::GetVersion.md)|Recupera el número de versión del estado almacenado de barra.|  
|[CDockState::LoadState](../Topic/CDockState::LoadState.md)|Información de estado de recupera del registro o archivo de .INI.|  
|[CDockState::SaveState](../Topic/CDockState::SaveState.md)|Guarda información de estado en el registro o en el archivo INI.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDockState::m\_arrBarInfo](../Topic/CDockState::m_arrBarInfo.md)|Matriz de punteros a la información de estado almacenado de vinculación con una entrada para cada barra de control.|  
  
## Comentarios  
 El estado de vinculación se incluyen el tamaño y la posición de la barra e indica si está acoplada.  Al recuperar al estado almacenado de acoplamiento, `CDockState` comprueba la barra no está visible con los valores actuales de la pantalla, `CDockState` de barra la posición y, si la escala de la posición de la barra de modo que esté visible.  El propósito principal de `CDockState` es guardar el estado completa de varias barras de controles y permitir que guarden ese estado y carga del registro, el archivo de .INI de la aplicación, o en formato binario como parte del contenido de un objeto de `CArchive` .  
  
 La barra puede ser cualquier barra de control acoplables, incluida una barra de herramientas, una barra de estado, o una barra de cuadro de diálogo.  Los objetos de`CDockState` se escriben y lectura de o desde un archivo con un objeto de `CArchive` .  
  
 [CFrameWnd::GetDockState](../Topic/CFrameWnd::GetDockState.md) recupera información de estado de `CControlBar` de toda la ventana de marco se opone y lo coloca en el objeto de `CDockState` .  Puede escribir el contenido del objeto de `CDockState` el almacenamiento con [serialice](../Topic/CObject::Serialize.md) o [CDockState::SaveState](../Topic/CDockState::SaveState.md).  Si desea restablecer posteriormente el estado de las barras de controles en la ventana de marco, puede cargar el estado con `Serialize` o [CDockState::LoadState](../Topic/CDockState::LoadState.md), utiliza [CFrameWnd::SetDockState](../Topic/CFrameWnd::SetDockState.md) para aplicar el estado guardado a las barras de control de la ventana de marco.  
  
 Para obtener más información sobre acoplar barras de controles, vea los artículos [Barras de controles](../../mfc/control-bars.md), [barras de herramientas: El acoplamiento y flotante](../../mfc/docking-and-floating-toolbars.md), y [cuadro Windows](../../mfc/frame-windows.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDockState`  
  
## Requisitos  
 **encabezado:** afxadv.h  
  
## Vea también  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)