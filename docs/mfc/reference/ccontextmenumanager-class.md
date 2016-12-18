---
title: "CContextMenuManager Class | Microsoft Docs"
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
  - "CContextMenuManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CContextMenuManager class"
ms.assetid: 1de20640-243c-47e1-85de-1baa4153bc83
caps.latest.revision: 32
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CContextMenuManager Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El objeto de `CContextMenuManager` administra los menús contextuales, también conocidos como menús contextuales.  
  
## Sintaxis  
  
```  
class CContextMenuManager : public CObject  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CContextMenuManager::CContextMenuManager](../Topic/CContextMenuManager::CContextMenuManager.md)|Crea un objeto `CContextMenuManager`.|  
|`CContextMenuManager::~CContextMenuManager`|Un destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CContextMenuManager::AddMenu](../Topic/CContextMenuManager::AddMenu.md)|Agrega un nuevo menú contextual.|  
|[CContextMenuManager::GetMenuById](../Topic/CContextMenuManager::GetMenuById.md)|Devuelve un identificador al menú asociado a la identificación proporcionada de recursos|  
|[CContextMenuManager::GetMenuByName](../Topic/CContextMenuManager::GetMenuByName.md)|Devuelve un identificador al menú que coincide con el nombre de menú proporcionado.|  
|[CContextMenuManager::GetMenuNames](../Topic/CContextMenuManager::GetMenuNames.md)|Devuelve una lista de nombres de menú.|  
|[CContextMenuManager::LoadState](../Topic/CContextMenuManager::LoadState.md)|Carga los menús contextuales almacenados en el Registro de Windows.|  
|[CContextMenuManager::ResetState](../Topic/CContextMenuManager::ResetState.md)|Borra los menús contextuales del administrador del menú contextual.|  
|[CContextMenuManager::SaveState](../Topic/CContextMenuManager::SaveState.md)|Guarda menús contextuales al Registro de Windows.|  
|[CContextMenuManager::SetDontCloseActiveMenu](../Topic/CContextMenuManager::SetDontCloseActiveMenu.md)|Controla si cierra `CContextMenuManager` el menú contextual activa cuando muestra un nuevo menú contextual.|  
|[CContextMenuManager::ShowPopupMenu](../Topic/CContextMenuManager::ShowPopupMenu.md)|Muestra el menú contextual especificado.|  
|[CContextMenuManager::TrackPopupMenu](../Topic/CContextMenuManager::TrackPopupMenu.md)|Muestra el menú contextual especificado.  Devuelve el índice del comando de menú seleccionado.|  
  
## Comentarios  
 `CContextMenuManager` administra menús contextuales y asegúrese de que tienen un aspecto coherente.  
  
 No debe crear un objeto de `CContextMenuManager` manualmente.  el marco de la aplicación crea el objeto de `CContextMenuManager` .  Sin embargo, debe llamar a [CWinAppEx::InitContextMenuManager](../Topic/CWinAppEx::InitContextMenuManager.md) cuando se inicializa la aplicación.  Después de inicializar el administrador de contexto, use el método [CWinAppEx::GetContextMenuManager](../Topic/CWinAppEx::GetContextMenuManager.md) para obtener un puntero al administrador de contexto para la aplicación.  
  
 Puede crear menús contextuales del runtime llamando a `AddMenu`.  Si desea mostrar el menú sin el primer datos proporcionados por el usuario que recibe, llame a `ShowPopupMenu`.  Se utiliza`TrackPopupMenu` cuando desee crear un menú y una espera para los datos proporcionados por el usuario.  `TrackPopupMenu` devuelve el índice del comando seleccionado o el 0 si el usuario queda sin seleccionar nada.  
  
 `CContextMenuManager` puede guardar y cargar su estado en el Registro de Windows.  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo agregar un menú a un objeto de `CContextMenuManager` , y cómo no cerrar un menú emergente activa cuando el objeto de `CContextMenuManager` muestra un nuevo menú emergente.  Este fragmento de código es parte de [Ejemplo de las páginas de personalizadas](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_CustomPages#4](../../mfc/reference/codesnippet/CPP/ccontextmenumanager-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CContextMenuManager](../../mfc/reference/ccontextmenumanager-class.md)  
  
## Requisitos  
 **encabezado:** afxcontextmenumanager.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx Class](../../mfc/reference/cwinappex-class.md)   
 [CWinAppEx::InitContextMenuManager](../Topic/CWinAppEx::InitContextMenuManager.md)