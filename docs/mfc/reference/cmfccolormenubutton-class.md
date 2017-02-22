---
title: "CMFCColorMenuButton Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCColorMenuButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCColorMenuButton class"
ms.assetid: 42685704-e994-4f7b-9553-62283c27b754
caps.latest.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 31
---
# CMFCColorMenuButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CMFCColorMenuButton` admite un comando de menú o un botón de la barra de herramientas que inicia un cuadro de diálogo Selector de colores.  
  
## Sintaxis  
  
```  
class CMFCColorMenuButton : public CMFCToolBarMenuButton  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCColorMenuButton::CMFCColorMenuButton](../Topic/CMFCColorMenuButton::CMFCColorMenuButton.md)|Crea un objeto `CMFCColorMenuButton`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCColorMenuButton::EnableAutomaticButton](../Topic/CMFCColorMenuButton::EnableAutomaticButton.md)|Habilita y deshabilita un botón “automático” que se coloque sobre los botones de color regulares.  \(El botón automático de sistema estándar se etiqueta **Automático**.\)|  
|[CMFCColorMenuButton::EnableDocumentColors](../Topic/CMFCColorMenuButton::EnableDocumentColors.md)|Permite la presentación de colores documento\-específicos en lugar de colores del sistema.|  
|[CMFCColorMenuButton::EnableOtherButton](../Topic/CMFCColorMenuButton::EnableOtherButton.md)|Habilita y deshabilita “other” botón que se coloque debajo de los botones de color regulares.  \(El sistema estándar de El “other” botón se etiqueta **más colores…**.\)|  
|[CMFCColorMenuButton::EnableTearOff](../Topic/CMFCColorMenuButton::EnableTearOff.md)|Habilita la capacidad de rasgar desactivado un panel de color.|  
|[CMFCColorMenuButton::GetAutomaticColor](../Topic/CMFCColorMenuButton::GetAutomaticColor.md)|Recupera el color automático actual.|  
|[CMFCColorMenuButton::GetColor](../Topic/CMFCColorMenuButton::GetColor.md)|Recupera el color actual del botón.|  
|[CMFCColorMenuButton::GetColorByCmdID](../Topic/CMFCColorMenuButton::GetColorByCmdID.md)|Recupera el color que corresponde a un identificador especificada de comando|  
|[CMFCColorMenuButton::OnChangeParentWnd](../Topic/CMFCColorMenuButton::OnChangeParentWnd.md)|Llamado por el marco cuando la ventana primaria.|  
|[CMFCColorMenuButton::OpenColorDialog](../Topic/CMFCColorMenuButton::OpenColorDialog.md)|Abre un cuadro de diálogo de selección de color.|  
|[CMFCColorMenuButton::SetColor](../Topic/CMFCColorMenuButton::SetColor.md)|Establece el color del botón en el color actual.|  
|[CMFCColorMenuButton::SetColorByCmdID](../Topic/CMFCColorMenuButton::SetColorByCmdID.md)|Establece el color del botón especificado del menú de color.|  
|[CMFCColorMenuButton::SetColorName](../Topic/CMFCColorMenuButton::SetColorName.md)|Establece un nuevo nombre para el color especificado.|  
|[CMFCColorMenuButton::SetColumnsNumber](../Topic/CMFCColorMenuButton::SetColumnsNumber.md)|Establece el número de columnas que aparezcan por un objeto de `CMFCColorBar` .|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCColorMenuButton::CopyFrom](../Topic/CMFCColorMenuButton::CopyFrom.md)|Copia otro botón de la barra de herramientas para el botón actual.|  
|[CMFCColorMenuButton::CreatePopupMenu](../Topic/CMFCColorMenuButton::CreatePopupMenu.md)|Crea un cuadro de diálogo selector de colores.|  
|[CMFCColorMenuButton::IsEmptyMenuAllowed](../Topic/CMFCColorMenuButton::IsEmptyMenuAllowed.md)|Indica si los menús vacíos se admiten.|  
|[CMFCColorMenuButton::OnDraw](../Topic/CMFCColorMenuButton::OnDraw.md)|Llamado por el marco para mostrar una imagen en un botón.|  
|[CMFCColorMenuButton::OnDrawOnCustomizeList](../Topic/CMFCColorMenuButton::OnDrawOnCustomizeList.md)|Llamado por el marco antes de que un objeto de `CMFCColorMenuButton` se muestra en la lista de un cuadro de diálogo personalización de la barra de herramientas.|  
  
## Comentarios  
 Para reemplazar el comando de menú o el botón de la barra de herramientas original con un objeto de `CMFCColorMenuButton` , cree el objeto de `CMFCColorMenuButton` , establezca cualquier estilo adecuado de [CMFCColorBar Class](../../mfc/reference/cmfccolorbar-class.md) , y llame al método de `ReplaceButton` de la clase de [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md) .  Si personaliza una barra de herramientas, llame al método de [CMFCToolBarsCustomizeDialog::ReplaceButton](../Topic/CMFCToolBarsCustomizeDialog::ReplaceButton.md) .  
  
 El cuadro de diálogo Selector de colores se crea durante el procesamiento del controlador de eventos [CMFCColorMenuButton::CreatePopupMenu](../Topic/CMFCColorMenuButton::CreatePopupMenu.md) .  El controlador de eventos notifica el cuadro primario con un mensaje de `WM_COMMAND` .  El objeto de `CMFCColorMenuButton` envía el id. del control que se asigna al comando de menú o el botón de la barra de herramientas original.  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo crear y configurar un botón de menú de color mediante varios métodos en la clase de `CMFCColorMenuButton` .  En el ejemplo, un objeto de `CPalette` se crea por primera vez y después se utiliza para construir un objeto de clase de `CMFCColorMenuButton` .  El objeto de `CMFCColorMenuButton` se configurado habilitar los botones automáticos y otros, y estableciendo el color y el número de columnas.  Este código es parte de [Ejemplo de pista de word](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_WordPad#5](../../mfc/reference/codesnippet/CPP/cmfccolormenubutton-class_1.h)]  
[!code-cpp[NVC_MFC_WordPad#6](../../mfc/reference/codesnippet/CPP/cmfccolormenubutton-class_2.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)  
  
 [CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md)  
  
## Requisitos  
 **encabezado:** afxcolormenubutton.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCColorBar Class](../../mfc/reference/cmfccolorbar-class.md)   
 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarsCustomizeDialog Class](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)   
 [CMFCColorButton Class](../../mfc/reference/cmfccolorbutton-class.md)