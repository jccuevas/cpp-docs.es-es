---
title: "CMFCRibbonQuickAccessToolBarDefaultState Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCRibbonQuickAccessToolBarDefaultState"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonQuickAccessToolBarDefaultState class"
ms.assetid: eca99200-b87b-47ba-b2e8-2f3f2444b176
caps.latest.revision: 28
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 30
---
# CMFCRibbonQuickAccessToolBarDefaultState Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una clase auxiliar que administra el estado predeterminada para la barra de herramientas de acceso rápido que se coloca en la barra de la cinta \([CMFCRibbonBar Class](../../mfc/reference/cmfcribbonbar-class.md)\).  
  
## Sintaxis  
  
```  
class CMFCRibbonQuickAccessToolBarDefaultState  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState](../Topic/CMFCRibbonQuickAccessToolBarDefaultState::CMFCRibbonQuickAccessToolBarDefaultState.md)|Crea un objeto `CMFCRibbonQuickAccessToolbarDefaultState`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonQuickAccessToolBarDefaultState::AddCommand](../Topic/CMFCRibbonQuickAccessToolBarDefaultState::AddCommand.md)|Agrega un comando al estado predeterminado de la barra de herramientas de acceso rápido.  Esto no cambia la propia barra de herramientas.|  
|[CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom](../Topic/CMFCRibbonQuickAccessToolBarDefaultState::CopyFrom.md)|copia las propiedades de una barra de herramientas de acceso rápido a otra.|  
|[CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll](../Topic/CMFCRibbonQuickAccessToolBarDefaultState::RemoveAll.md)|quita todos los comandos de la barra de herramientas de acceso rápido.  Esto no cambia la propia barra de herramientas.|  
  
## Comentarios  
 Después de crear la barra de herramientas de acceso rápido en la aplicación, se recomienda establecer su estado predeterminado llamando a [CMFCRibbonBar::SetQuickAccessDefaultState](../Topic/CMFCRibbonBar::SetQuickAccessDefaultState.md).  Restablece en este estado predeterminada cuando un usuario hace clic en el botón de **Restablecer** en la página de **Personalizar** del cuadro de diálogo de **Opciones** de la aplicación.  
  
## Jerarquía de herencia  
 [CMFCRibbonQuickAccessToolBarDefaultState](../../mfc/reference/cmfcribbonquickaccesstoolbardefaultstate-class.md)  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo construir un objeto de clase de `CMFCRibbonQuickAccessToolbarDefaultState` y cómo agregar un comando al estado predeterminado de la barra de herramientas de acceso rápido.  
  
 [!code-cpp[NVC_MFC_RibbonApp#21](../../mfc/reference/codesnippet/CPP/cmfcribbonquickaccesstoolbardefaultstate-class_1.cpp)]  
  
## Requisitos  
 **encabezado:** afxribbonquickaccesstoolbar.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonBar Class](../../mfc/reference/cmfcribbonbar-class.md)   
 [CMFCRibbonBar::SetQuickAccessDefaultState](../Topic/CMFCRibbonBar::SetQuickAccessDefaultState.md)