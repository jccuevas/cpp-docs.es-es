---
title: "CMDITabInfo Class | Microsoft Docs"
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
  - "CMDITabInfo"
  - "CMDITabInfo.CMDITabInfo"
  - "CMDITabInfo::CMDITabInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMDITabInfo class"
  - "CMDITabInfo class, constructor"
ms.assetid: 988ae1b7-4f7f-4239-b88f-7e28b3291c5e
caps.latest.revision: 37
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMDITabInfo Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CMDITabInfo` se utiliza para pasar parámetros al método de [CMDIFrameWndEx::EnableMDITabbedGroups](../Topic/CMDIFrameWndEx::EnableMDITabbedGroups.md) .  Establezca los miembros de esta clase para controlar el comportamiento de MDI con grupos.  
  
## Sintaxis  
  
```  
class CMDITabInfo   
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMDITabInfo::CMDITabInfo`|Constructor predeterminado.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMDITabInfo::Serialize](../Topic/CMDITabInfo::Serialize.md)|Lee o escribe este objeto o un archivo.|  
  
### miembros de datos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMDITabInfo::m\_bActiveTabCloseButton;](../Topic/CMDITabInfo::m_bActiveTabCloseButton;.md)|Especifica si un botón de **Cerrar** se muestra en la etiqueta de la pestaña activa.|  
|[CMDITabInfo::m\_bAutoColor](../Topic/CMDITabInfo::m_bAutoColor.md)|Especifica si un color pestañas de MDI.|  
|[CMDITabInfo::m\_bDocumentMenu](../Topic/CMDITabInfo::m_bDocumentMenu.md)|Especifica si el grupo de la pestaña muestra un menú emergente que muestra una lista de documentos abiertos o mostrar los botones de navegación.|  
|[CMDITabInfo::m\_bEnableTabSwap](../Topic/CMDITabInfo::m_bEnableTabSwap.md)|Especifica si el usuario puede cambiar las posiciones de tabulaciones arrastrando.|  
|[CMDITabInfo::m\_bFlatFrame](../Topic/CMDITabInfo::m_bFlatFrame.md)|especifica si las fichas tienen un cuadro plano.|  
|[CMDITabInfo::m\_bTabCloseButton](../Topic/CMDITabInfo::m_bTabCloseButton.md)|Especifica si cada etiqueta de la ficha muestra un botón de **Cerrar** .|  
|[CMDITabInfo::m\_bTabCustomTooltips](../Topic/CMDITabInfo::m_bTabCustomTooltips.md)|Especifica si la información sobre herramientas personalizadas están habilitadas.|  
|[CMDITabInfo::m\_bTabIcons](../Topic/CMDITabInfo::m_bTabIcons.md)|Especifica si mostrar iconos en las pestañas de MDI.|  
|[CMDITabInfo::m\_nTabBorderSize](../Topic/CMDITabInfo::m_nTabBorderSize.md)|Especifica el tamaño del borde de cada ventana de la pestaña.|  
|[CMDITabInfo::m\_style](../Topic/CMDITabInfo::m_style.md)|Especifica el estilo de las etiquetas de la pestaña.|  
|[CMDITabInfo::m\_tabLocation](../Topic/CMDITabInfo::m_tabLocation.md)|Especifica si las etiquetas de las pestañas se encuentran en la parte superior o inferior de la página.|  
  
## Comentarios  
 Esta clase especifica los parámetros de los grupos de la pestaña MDI que el marco de trabajo crea.  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo establecer los valores de las variables diferentes miembros de la clase de `CMDITabInfo` .  
  
 [!code-cpp[NVC_MFC_MDITab#1](../../mfc/reference/codesnippet/CPP/cmditabinfo-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CMDITabInfo](../../mfc/reference/cmditabinfo-class.md)  
  
## Requisitos  
 **encabezado:** afxmdiclientareawnd.h  
  
## Vea también  
 [CMDIFrameWndEx \(Clase\)](../../mfc/reference/cmdiframewndex-class.md)   
 [Grupos con pestañas MDI](../../mfc/mdi-tabbed-groups.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)