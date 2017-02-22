---
title: "CMFCRibbonMainPanel Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCRibbonMainPanel"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonMainPanel class"
ms.assetid: 1af78798-5e75-4365-9c81-a54aa5679602
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CMFCRibbonMainPanel Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa un panel de cinta de opciones que muestra al hacer clic en [CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md).  
  
## Sintaxis  
  
```  
class CMFCRibbonMainPanel : public CMFCRibbonPanel  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCRibbonMainPanel::CMFCRibbonMainPanel`|Constructor predeterminado.|  
|`CMFCRibbonMainPanel::~CMFCRibbonMainPanel`|Un destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonMainPanel::Add](../Topic/CMFCRibbonMainPanel::Add.md)|Agrega un elemento de cinta de opciones al panel izquierdo del panel del botón de la aplicación.  \(Reemplaza [CMFCRibbonPanel::Add](../Topic/CMFCRibbonPanel::Add.md).\)|  
|[CMFCRibbonMainPanel::AddRecentFilesList](../Topic/CMFCRibbonMainPanel::AddRecentFilesList.md)|Agrega una cadena de texto al menú reciente de la lista de archivos.|  
|[CMFCRibbonMainPanel::AddToBottom](../Topic/CMFCRibbonMainPanel::AddToBottom.md)|Agrega un elemento cinta a la sección inferior del panel de la aplicación de la cinta de opciones.|  
|[CMFCRibbonMainPanel::AddToRight](../Topic/CMFCRibbonMainPanel::AddToRight.md)|Agrega un elemento cinta el panel derecho del panel del botón de la aplicación.|  
|`CMFCRibbonMainPanel::CreateObject`|Utiliza el marco para crear una instancia dinámica de este tipo de clase.|  
|[CMFCRibbonMainPanel::GetCommandsFrame](../Topic/CMFCRibbonMainPanel::GetCommandsFrame.md)|Devuelve un rectángulo que representa el área del panel de la cinta de opciones.|  
|`CMFCRibbonMainPanel::GetThisClass`|Utiliza el marco para obtener un puntero al objeto de [Recursos](../../mfc/reference/cruntimeclass-structure.md) que está asociado a este tipo de clase.|  
  
## Comentarios  
 El marco muestra `CMFCRibbonMainPanel` cuando se abre el panel de la aplicación.  Contiene tres paneles:  
  
-   El panel izquierdo contiene los comandos asociados a archivos, como **Abrir**, **Guardar**, **Impresión**, y **Cerrar**.  Para agregar un comando a este panel, llame a [CMFCRibbonMainPanel::Add](../Topic/CMFCRibbonMainPanel::Add.md).  
  
-   El panel derecho contiene valores que modifican el comando que hace clic en el panel izquierdo.  Por ejemplo, si hace clic en **Guardar como** del panel izquierdo, el panel derecho puede mostrar tipos de archivos disponibles.  Para agregar un elemento a este panel, llame a [CMFCRibbonMainPanel::AddToRight](../Topic/CMFCRibbonMainPanel::AddToRight.md).  
  
-   El panel inferior contiene botones que permiten cambiar la configuración de la aplicación y que el programa.  Para agregar un elemento a este panel, llame a [CMFCRibbonMainPanel::AddToBottom](../Topic/CMFCRibbonMainPanel::AddToBottom.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)  
  
 [CMFCRibbonMainPanel](../../mfc/reference/cmfcribbonmainpanel-class.md)  
  
## Requisitos  
 **encabezado:** afxRibbonMainPanel.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonPanel Class](../../mfc/reference/cmfcribbonpanel-class.md)