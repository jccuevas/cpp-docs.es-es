---
title: "CMouseManager Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMouseManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMouseManager class"
ms.assetid: a4d05017-4e44-4a40-8b57-4ece0de20481
caps.latest.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 28
---
# CMouseManager Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Permite que un usuario asociar comandos diferentes con un determinado objeto de [CView](../../mfc/reference/cview-class.md) cuando el usuario hace doble clic en el interior que vean.  
  
## Sintaxis  
  
```  
class CMouseManager : public CObject  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMouseManager::AddView](../Topic/CMouseManager::AddView.md)|Agrega un objeto de `CView` al cuadro de diálogo de **personalización** .  El cuadro de diálogo de **personalización** permita asociar un doble clic con un comando para cada una de las vistas mencionadas.|  
|[CMouseManager::GetViewDblClickCommand](../Topic/CMouseManager::GetViewDblClickCommand.md)|Devuelve el comando que se ejecuta cuando el usuario hace doble clic dentro visualización proporcionada.|  
|[CMouseManager::GetViewIconId](../Topic/CMouseManager::GetViewIconId.md)|Devuelve el icono asociado al identificador proporcionada de vista|  
|[CMouseManager::GetViewIdByName](../Topic/CMouseManager::GetViewIdByName.md)|Devuelve el identificador de la vista asociado al nombre de vista proporcionado.|  
|[CMouseManager::GetViewNames](../Topic/CMouseManager::GetViewNames.md)|recupera una lista de todos los nombres de vista agregados.|  
|[CMouseManager::LoadState](../Topic/CMouseManager::LoadState.md)|Carga el estado de `CMouseManager` del Registro de Windows.|  
|[CMouseManager::SaveState](../Topic/CMouseManager::SaveState.md)|Escribe el estado de `CMouseManager` al Registro de Windows.|  
|[CMouseManager::SetCommandForDblClk](../Topic/CMouseManager::SetCommandForDblClk.md)|Asocia el comando proporcionado y visualización proporcionada.|  
  
## Comentarios  
 La clase de `CMouseManager` mantiene una colección de objetos `CView` .  Cada vista se identifica mediante un nombre y por un identificador  Estas vistas se muestran en el cuadro de diálogo de **personalización** .  El usuario puede cambiar el comando que está asociado con cualquier vista a través del cuadro de diálogo de **personalización** .  Se ejecuta el comando asociado cuando el usuario hace doble clic en esa vista.  Para ello desde una perspectiva de programación, debe procesar el mensaje de `WM_LBUTTONDBLCLK` y llamar a la función de [CWinAppEx::OnViewDoubleClick](../Topic/CWinAppEx::OnViewDoubleClick.md) en el código para ese objeto de `CView` .  
  
 No debe crear un objeto de `CMouseManager` manualmente.  Se crea el marco de la aplicación.  También se destruida automáticamente cuando el usuario sale de la aplicación.  Para obtener un puntero al administrador del mouse para la aplicación, llame a [CWinAppEx::GetMouseManager](../Topic/CWinAppEx::GetMouseManager.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMouseManager](../../mfc/reference/cmousemanager-class.md)  
  
## Requisitos  
 **encabezado:** afxmousemanager.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx Class](../../mfc/reference/cwinappex-class.md)   
 [Personalización del teclado y del mouse](../../mfc/keyboard-and-mouse-customization.md)