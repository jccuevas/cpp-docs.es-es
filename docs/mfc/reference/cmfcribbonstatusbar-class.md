---
title: "CMFCRibbonStatusBar Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCRibbonStatusBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonStatusBar class"
ms.assetid: 921eb57f-3b40-49fa-a38c-3f2fb6dc2893
caps.latest.revision: 37
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 39
---
# CMFCRibbonStatusBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CMFCRibbonStatusBar` implementa un control de barra de estado que puede mostrar elementos de cinta de opciones.  
  
## Sintaxis  
  
```  
class CMFCRibbonStatusBar : public CMFCRibbonBar  
```  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonStatusBar::AddDynamicElement](../Topic/CMFCRibbonStatusBar::AddDynamicElement.md)|agrega un elemento dinámico a la barra de estado de la cinta de opciones.|  
|[CMFCRibbonStatusBar::AddElement](../Topic/CMFCRibbonStatusBar::AddElement.md)|Agrega un nuevo elemento cinta a la barra de estado de la cinta de opciones.|  
|[CMFCRibbonStatusBar::AddExtendedElement](../Topic/CMFCRibbonStatusBar::AddExtendedElement.md)|Agrega un elemento de cinta de opciones al área extendida de la barra de estado de la cinta de opciones.|  
|[CMFCRibbonStatusBar::AddSeparator](../Topic/CMFCRibbonStatusBar::AddSeparator.md)|agrega un separador a la barra de estado de la cinta de opciones.|  
|[CMFCRibbonStatusBar::Create](../Topic/CMFCRibbonStatusBar::Create.md)|crea una barra de estado de la cinta de opciones.|  
|[CMFCRibbonStatusBar::CreateEx](../Topic/CMFCRibbonStatusBar::CreateEx.md)|crea una barra de estado de la cinta de opciones con un estilo extendido.|  
|[CMFCRibbonStatusBar::FindByID](../Topic/CMFCRibbonStatusBar::FindByID.md)||  
|[CMFCRibbonStatusBar::FindElement](../Topic/CMFCRibbonStatusBar::FindElement.md)|Devuelve un puntero al elemento que tiene el identificador especificado de comando|  
|[CMFCRibbonStatusBar::GetCount](../Topic/CMFCRibbonStatusBar::GetCount.md)|Devuelve el número de elementos que se encuentran en el área principal de barra de estado de la cinta de opciones.|  
|[CMFCRibbonStatusBar::GetElement](../Topic/CMFCRibbonStatusBar::GetElement.md)|Devuelve un puntero al elemento que se encuentra en el índice especificado.|  
|[CMFCRibbonStatusBar::GetExCount](../Topic/CMFCRibbonStatusBar::GetExCount.md)|Devuelve el número de elementos que se encuentran en el área extendida de la barra de estado de la cinta de opciones.|  
|[CMFCRibbonStatusBar::GetExElement](../Topic/CMFCRibbonStatusBar::GetExElement.md)|Devuelve un puntero al elemento que se encuentra en el índice especificado en el área extendida de la barra de estado de la cinta de opciones.|  
|[CMFCRibbonStatusBar::GetExtendedArea](../Topic/CMFCRibbonStatusBar::GetExtendedArea.md)||  
|[CMFCRibbonStatusBar::GetSpace](../Topic/CMFCRibbonStatusBar::GetSpace.md)||  
|[CMFCRibbonStatusBar::IsBottomFrame](../Topic/CMFCRibbonStatusBar::IsBottomFrame.md)||  
|[CMFCRibbonStatusBar::IsExtendedElement](../Topic/CMFCRibbonStatusBar::IsExtendedElement.md)||  
|[CMFCRibbonStatusBar::IsInformationMode](../Topic/CMFCRibbonStatusBar::IsInformationMode.md)|Determina si se habilita el modo de información para la barra de estado de la cinta de opciones.|  
|[CMFCRibbonStatusBar::RecalcLayout](../Topic/CMFCRibbonStatusBar::RecalcLayout.md)|\(Reemplaza [CMFCRibbonBar::RecalcLayout](../Topic/CMFCRibbonBar::RecalcLayout.md).\)|  
|[CMFCRibbonStatusBar::RemoveAll](../Topic/CMFCRibbonStatusBar::RemoveAll.md)|Quita todos los elementos de barra de estado de la cinta de opciones.|  
|[CMFCRibbonStatusBar::RemoveElement](../Topic/CMFCRibbonStatusBar::RemoveElement.md)|Quita el elemento que tiene un identificador especificado de comando de la barra de estado de la cinta de opciones.|  
|[CMFCRibbonStatusBar::SetInformation](../Topic/CMFCRibbonStatusBar::SetInformation.md)|Habilita o deshabilita el modo de información para la barra de estado de la cinta de opciones.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonStatusBar::OnDrawInformation](../Topic/CMFCRibbonStatusBar::OnDrawInformation.md)|Muestra la cadena de información que aparece en la barra de estado de la cinta cuando se habilita el modo de información.|  
  
## Comentarios  
 Los usuarios pueden cambiar la visibilidad de los elementos de la cinta en una barra de estado de la cinta de opciones mediante el menú contextual integrado para la barra de estado de la cinta de opciones.  Puede agregar o quitar elementos dinámicamente.  
  
 Una barra de estado de la cinta tiene dos áreas: un área principal y un área extendida.  El área extendida se muestra a la derecha de la barra de estado de la cinta de opciones y aparece en un color diferente que el área principal.  
  
 Normalmente, el área principal de la barra de estado muestra notificaciones de estado, y controles extendidos de la vista del área.  El área extendida permanece visible en todo momento posible cuando el usuario cambia el tamaño de la barra de estado de la cinta de opciones.  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo utilizar varios métodos en la clase de `CMFCRibbonStatusBar` .  El ejemplo muestra cómo agregar un nuevo elemento cinta a la barra de estado de la cinta de opciones, agregar un elemento cinta al área extendida de la barra de estado de la cinta de opciones, agregar un separador, y habilitar el modo normal para la barra de estado de la cinta de opciones.  
  
 [!code-cpp[NVC_MFC_RibbonApp#15](../../mfc/reference/codesnippet/CPP/cmfcribbonstatusbar-class_1.cpp)]  
[!code-cpp[NVC_MFC_RibbonApp#16](../../mfc/reference/codesnippet/CPP/cmfcribbonstatusbar-class_2.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)  
  
 [CMFCRibbonStatusBar](../../mfc/reference/cmfcribbonstatusbar-class.md)  
  
## Requisitos  
 **encabezado:** afxribbonstatusbar.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonBar Class](../../mfc/reference/cmfcribbonbar-class.md)   
 [CMFCRibbonBaseElement Class](../../mfc/reference/cmfcribbonbaseelement-class.md)   
 [CMFCRibbonBar Class](../../mfc/reference/cmfcribbonbar-class.md)