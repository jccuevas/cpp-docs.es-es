---
title: "CMFCBaseVisualManager Class | Microsoft Docs"
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
  - "CMFCBaseVisualManager"
  - "CMFCBaseVisualManager.~CMFCBaseVisualManager"
  - "~CMFCBaseVisualManager"
  - "CMFCBaseVisualManager::~CMFCBaseVisualManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "~CMFCBaseVisualManager destructor"
  - "CMFCBaseVisualManager class"
  - "CMFCBaseVisualManager class, destructor"
ms.assetid: d56f3afc-cdea-4de1-825a-a08999c571e0
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCBaseVisualManager Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una capa entre los administradores visuales derivados y el tema API de Windows.  
  
 `CMFCBaseVisualManager` carga UxTheme.dll, si está disponible, y administra el acceso a los métodos de la API del tema de Windows.  
  
 Esta clase es sólo para uso interno.  
  
## Sintaxis  
  
```  
class CMFCBaseVisualManager: public CObject  
```  
  
## Members  
  
### Constructores públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|[CMFCBaseVisualManager::CMFCBaseVisualManager](../Topic/CMFCBaseVisualManager::CMFCBaseVisualManager.md)|Las construcciones e inicializan un objeto de `CMFCBaseVisualManager` .|  
|`CMFCBaseVisualManager::~CMFCBaseVisualManager`|Un destructor.|  
  
### Métodos públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|[CMFCBaseVisualManager::DrawCheckBox](../Topic/CMFCBaseVisualManager::DrawCheckBox.md)|Dibuja un control checkbox mediante el tema actual de Windows.|  
|[CMFCBaseVisualManager::DrawComboBorder](../Topic/CMFCBaseVisualManager::DrawComboBorder.md)|Dibuja un borde del cuadro combinado con el tema actual de Windows.|  
|[CMFCBaseVisualManager::DrawComboDropButton](../Topic/CMFCBaseVisualManager::DrawComboDropButton.md)|Dibuja un botón desplegable de cuadro combinado con el tema actual de Windows.|  
|[CMFCBaseVisualManager::DrawPushButton](../Topic/CMFCBaseVisualManager::DrawPushButton.md)|Dibuja un botón de comando con el tema actual de Windows.|  
|[CMFCBaseVisualManager::DrawRadioButton](../Topic/CMFCBaseVisualManager::DrawRadioButton.md)|Dibuja un control de botón de opción mediante el tema actual de Windows.|  
|[CMFCBaseVisualManager::DrawStatusBarProgress](../Topic/CMFCBaseVisualManager::DrawStatusBarProgress.md)|Dibuja una barra de progreso en un control de barra de estado \([CMFCStatusBar Class](../../mfc/reference/cmfcstatusbar-class.md)\) mediante el tema actual de Windows.|  
|[CMFCBaseVisualManager::FillReBarPane](../Topic/CMFCBaseVisualManager::FillReBarPane.md)|Rellena el fondo del control rebar mediante el tema actual de Windows.|  
|[CMFCBaseVisualManager::GetStandardWindowsTheme](../Topic/CMFCBaseVisualManager::GetStandardWindowsTheme.md)|obtiene el tema actual de Windows.|  
  
### Métodos protegidos  
  
|||  
|-|-|  
|Name|Descripción|  
|[CMFCBaseVisualManager::CleanUpThemes](../Topic/CMFCBaseVisualManager::CleanUpThemes.md)|Llama a `CloseThemeData` para todos los identificadores recopilados en `UpdateSystemColors`.|  
|[CMFCBaseVisualManager::UpdateSystemColors](../Topic/CMFCBaseVisualManager::UpdateSystemColors.md)|Llamadas `OpenThemeData` para obtener los identificadores para dibujar varios controles: ventanas, barras de herramientas, botones, etc.|  
  
## Comentarios  
 No tiene que crear instancias de objetos de esta clase directamente.  
  
 Porque es una clase base para todos los administradores visuales, basta con llamar a [CMFCVisualManager::GetInstance](../Topic/CMFCVisualManager::GetInstance.md), obtiene un puntero al administrador Visual actual, y tiene acceso a los métodos para `CMFCBaseVisualManager` con ese puntero.  Sin embargo, si tiene que mostrar un control mediante el tema actual de Windows, es preferible utilizar la interfaz de `CMFCVisualManagerWindows` .  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)  
  
## Requisitos  
 **encabezado:** afxvisualmanager.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)