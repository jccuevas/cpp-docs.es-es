---
title: "Estilos de control ToolBar | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "estilos de control ToolBar"
ms.assetid: 0f717eb9-fa32-4263-b852-809238863feb
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# Estilos de control ToolBar
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[CMFCToolBarButton Class](../../mfc/reference/cmfctoolbarbutton-class.md) tiene un conjunto de indicadores de estilo que determinan el aspecto y el comportamiento del botón.  Puede definir una combinación de estos marcadores llamando a [CMFCToolBarButton::SetStyle](../Topic/CMFCToolBarButton::SetStyle.md).  En este tema se muestran los valores de marcador de estilo y sus significados.  
  
## Valores de propiedad  
 Los siguientes valores determinan el tipo de botón que el control representa:  
  
 TBBS\_BUTTON  
 Mismo botón estándar \(valor predeterminado\).  
  
 TBBS\_CHECKBOX  
 Casilla.  
  
 TBBS\_CHECKGROUP  
 El inicio de un grupo de casillas.  
  
 TBBS\_GROUP  
 El inicio de un grupo de botones.  
  
 TBBS\_SEPARATOR  
 Separador.  
  
 Los valores siguientes representan el estado actual del control:  
  
 TBBS\_CHECKED  
 La casilla está activada.  
  
 TBBS\_DISABLED  
 Se deshabilita el Control.  
  
 TBBS\_INDETERMINATE  
 La casilla está en un estado indeterminado.  
  
 TBBS\_PRESSED  
 Se presiona el botón.  
  
 El valor siguiente cambia el diseño del botón en la barra de herramientas:  
  
 TBBS\_BREAK  
 Coloca el elemento en una nueva línea o en una nueva columna sin separar columnas.  
  
## Comentarios  
 El estilo actual se almacena en [CMFCToolBarButton::m\_nStyle](../Topic/CMFCToolBarButton::m_nStyle.md).  No establezca un nuevo valor en `m_nStyle` directamente, porque algunas clases derivadas realizan el procesamiento adicional cuando se llama a `SetStyles`.  
  
 El administrador visual determina la apariencia de botones en cada estado.  Para obtener más información, vea [Administrador de visualización](../../mfc/visualization-manager.md).  
  
## Requisitos  
 **Encabezado:** afxtoolbarbutton.h  
  
## Vea también  
 [Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)   
 [CMFCToolBarButton Class](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [Administrador de visualización](../../mfc/visualization-manager.md)