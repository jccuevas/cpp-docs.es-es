---
title: "CMFCColorBar Class | Microsoft Docs"
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
  - "CMFCColorBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCColorBar class"
  - "CMFCColorBar::m_bInternal data member"
  - "CMFCColorBar::m_bIsEnabled data member"
  - "CMFCColorBar::m_bIsTearOff data member"
  - "CMFCColorBar::m_BoxSize data member"
  - "CMFCColorBar::m_bShowDocColorsWhenDocked data member"
  - "CMFCColorBar::m_bStdColorDlg data member"
  - "CMFCColorBar::m_ColorAutomatic data member"
  - "CMFCColorBar::m_ColorNames data member"
  - "CMFCColorBar::m_colors data member"
  - "CMFCColorBar::m_ColorSelected data member"
  - "CMFCColorBar::m_lstDocColors data member"
  - "CMFCColorBar::m_nCommandID data member"
  - "CMFCColorBar::m_nHorzMargin data member"
  - "CMFCColorBar::m_nHorzOffset data member"
  - "CMFCColorBar::m_nNumColumns data member"
  - "CMFCColorBar::m_nNumColumnsVert data member"
  - "CMFCColorBar::m_nNumRowsHorz data member"
  - "CMFCColorBar::m_nRowHeight data member"
  - "CMFCColorBar::m_nVertMargin data member"
  - "CMFCColorBar::m_nVertOffset data member"
  - "CMFCColorBar::m_Palette data member"
  - "CMFCColorBar::m_pParentBtn data member"
  - "CMFCColorBar::m_pParentRibbonBtn data member"
  - "CMFCColorBar::m_pWndPropList data member"
  - "CMFCColorBar::m_strAutoColor data member"
  - "CMFCColorBar::m_strDocColors data member"
  - "CMFCColorBar::m_strOtherColor data member"
ms.assetid: 4756ee40-25a5-4cee-af7f-acab7993d1c7
caps.latest.revision: 35
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCColorBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CMFCColorBar` representa una barra de controles de acoplamiento que puede seleccionar colores en un documento o aplicación.  
  
## Sintaxis  
  
```  
class CMFCColorBar : public CMFCPopupMenuBar  
```  
  
## Members  
  
### Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCColorBar::CMFCColorBar](../Topic/CMFCColorBar::CMFCColorBar.md)|Crea un objeto `CMFCColorBar`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCColorBar::ContextToSize](../Topic/CMFCColorBar::ContextToSize.md)|Calcula los márgenes verticales y horizontales necesarios para contener los botones del control de barra de color y ajustar la ubicación de los botones.|  
|[CMFCColorBar::CreateControl](../Topic/CMFCColorBar::CreateControl.md)|Crea una ventana de control de la barra de color, la asocia el objeto de `CMFCColorBar` , y cambia el tamaño del control para contener la paleta especificada de colores.|  
|[CMFCColorBar::Create](../Topic/CMFCColorBar::Create.md)|Crea una ventana de control de la barra de color y la agrega al objeto de `CMFCColorBar` .|  
|[CMFCColorBar::EnableAutomaticButton](../Topic/CMFCColorBar::EnableAutomaticButton.md)|Muestra u oculta el botón automático.|  
|[CMFCColorBar::EnableOtherButton](../Topic/CMFCColorBar::EnableOtherButton.md)|Habilita o deshabilita la presentación de un cuadro de diálogo que permite al usuario seleccionar más colores.|  
|[CMFCColorBar::GetColor](../Topic/CMFCColorBar::GetColor.md)|Recupera el color seleccionado actualmente.|  
|[CMFCColorBar::GetCommandID](../Topic/CMFCColorBar::GetCommandID.md)|Recupera el identificador del control actual de la barra de color.|  
|[CMFCColorBar::GetHighlightedColor](../Topic/CMFCColorBar::GetHighlightedColor.md)|Recupera el color que significa que un botón de color tiene el foco; es decir, el botón está *activo*.|  
|[CMFCColorBar::GetHorzMargin](../Topic/CMFCColorBar::GetHorzMargin.md)|Recupera el margen horizontal, que es el espacio entre la celda de color de la izquierda o la derecha y el límite del área cliente.|  
|[CMFCColorBar::GetVertMargin](../Topic/CMFCColorBar::GetVertMargin.md)|Recupera el margen vertical, que es el espacio entre la celda de color de la parte superior o inferior y el límite del área cliente.|  
|[CMFCColorBar::IsTearOff](../Topic/CMFCColorBar::IsTearOff.md)|Indica si la barra de color actual es acoplables.|  
|[CMFCColorBar::SetColor](../Topic/CMFCColorBar::SetColor.md)|Establece el color que está actualmente seleccionado.|  
|[CMFCColorBar::SetColorName](../Topic/CMFCColorBar::SetColorName.md)|Establece un nuevo nombre para el color especificado.|  
|[CMFCColorBar::SetCommandID](../Topic/CMFCColorBar::SetCommandID.md)|Establece un nuevo identificador de comando para un control de barra de color.|  
|[CMFCColorBar::SetDocumentColors](../Topic/CMFCColorBar::SetDocumentColors.md)|Establece la lista de colores que se utilizan en el documento actual.|  
|[CMFCColorBar::SetHorzMargin](../Topic/CMFCColorBar::SetHorzMargin.md)|Establece el margen horizontal, que es el espacio entre la celda de color de la izquierda o la derecha y el límite del área cliente.|  
|[CMFCColorBar::SetVertMargin](../Topic/CMFCColorBar::SetVertMargin.md)|Establece el margen vertical, que es el espacio entre la parte superior o inferior la celda en color y el límite de área cliente.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCColorBar::AdjustLocations](../Topic/CMFCColorBar::AdjustLocations.md)|Ajusta las posiciones de color respecto al control de barra de color.|  
|[CMFCColorBar::AllowChangeTextLabels](../Topic/CMFCColorBar::AllowChangeTextLabels.md)|Indica si la etiqueta de texto de botones de color puede cambiar.|  
|[CMFCColorBar::AllowShowOnList](../Topic/CMFCColorBar::AllowShowOnList.md)|Indica si el objeto de control de la barra de color puede aparecer en una lista de barras de herramientas durante el proceso de personalización.|  
|[CMFCColorBar::CalcSize](../Topic/CMFCColorBar::CalcSize.md)|Llamado por el marco como parte del proceso de cálculo de diseño.|  
|[CMFCColorBar::CreatePalette](../Topic/CMFCColorBar::CreatePalette.md)|Initalizes una paleta con los colores en una matriz de colores.|  
|[CMFCColorBar::GetColorGridSize](../Topic/CMFCColorBar::GetColorGridSize.md)|Calcula el número de filas y columnas en la cuadrícula de un control de barra de color.|  
|[CMFCColorBar::GetExtraHeight](../Topic/CMFCColorBar::GetExtraHeight.md)|Calcula el alto adicional que la barra de color actual requiere para mostrar elementos diferentes de la interfaz de usuario como el botón de **Otros** , documentan colores, y así sucesivamente.|  
|[CMFCColorBar::InitColors](../Topic/CMFCColorBar::InitColors.md)|Inicializa una matriz de colores con los colores de una paleta especificada o la paleta predeterminada del sistema.|  
|[CMFCColorBar::OnKey](../Topic/CMFCColorBar::OnKey.md)|Llamado por el marco cuando un usuario presiona un botón de teclado.|  
|[CMFCColorBar::OnSendCommand](../Topic/CMFCColorBar::OnSendCommand.md)|Llamado por el marco para cerrar una jerarquía de controles móviles.|  
|[CMFCColorBar::OnUpdateCmdUI](../Topic/CMFCColorBar::OnUpdateCmdUI.md)|Llamado por el marco para habilitar o deshabilitar un elemento de la interfaz de usuario de un control de barra de color antes de elemento se muestra.|  
|[CMFCColorBar::OpenColorDialog](../Topic/CMFCColorBar::OpenColorDialog.md)|Abre un cuadro de diálogo color.|  
|[CMFCColorBar::Rebuild](../Topic/CMFCColorBar::Rebuild.md)|Redibuja completamente el control de barra de color.|  
|[CMFCColorBar::SelectPalette](../Topic/CMFCColorBar::SelectPalette.md)|Establece la paleta lógica de contexto especificado de dispositivo con la paleta del botón primario del control actual de la barra de color.|  
|[CMFCColorBar::SetPropList](../Topic/CMFCColorBar::SetPropList.md)|Establezca el miembro de datos protegido `m_pWndPropList` el puntero especificado a un control de cuadrícula de propiedades.|  
|[CMFCColorBar::ShowCommandMessageString](../Topic/CMFCColorBar::ShowCommandMessageString.md)|Solicita la ventana de marco propietaria del control de barra de color para actualizar la línea de mensajes en la barra de estado.|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|`m_bInternal`|Un campo booleano que determina si los eventos del mouse se procesaron.  Normalmente, se procesan los eventos del mouse cuando este campo es `TRUE` y modo de personalización es `FALSE`.|  
|`m_bIsEnabled`|Un booleano que indica si un control está habilitado.|  
|`m_bIsTearOff`|Un booleano que indica si el control de barra de color admite el acoplamiento.|  
|`m_BoxSize`|Un objeto de [CSize](../../atl-mfc-shared/reference/csize-class.md) que especifica el tamaño de una celda en una cuadrícula de la barra de color.|  
|`m_bShowDocColorsWhenDocked`|Un booleano que indica si mostrar colores del documento cuando la barra de color está acoplada.  Para obtener más información, vea [CMFCColorBar::SetDocumentColors](../Topic/CMFCColorBar::SetDocumentColors.md).|  
|`m_bStdColorDlg`|Un booleano que indica si mostrar el cuadro de diálogo estándar del color del sistema o el cuadro de diálogo [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) .  Para obtener más información, vea [CMFCColorBar::EnableOtherButton](../Topic/CMFCColorBar::EnableOtherButton.md).|  
|`m_ColorAutomatic`|[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) que almacena color automático actual.  Para obtener más información, vea [CMFCColorBar::EnableOtherButton](../Topic/CMFCColorBar::EnableOtherButton.md).|  
|`m_ColorNames`|Un objeto de [CMap](../../mfc/reference/cmap-class.md) que asocia un conjunto de colores RGB a sus nombres.|  
|`m_colors`|[CArray](../../mfc/reference/carray-class.md) de los valores de [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) que contiene los colores que se muestran en el control de barra de color.|  
|`m_ColorSelected`|Un valor de [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) que es el color seleccionado por el usuario actualmente el control de barra de color.|  
|`m_lstDocColors`|[CList](../../mfc/reference/clist-class.md) de los valores de [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) que contiene los colores que se utilizan actualmente en un documento.|  
|`m_nCommandID`|Un entero sin signo que es el id. de comando de un botón de color.|  
|`m_nHorzMargin`|Un entero que es el margen horizontal entre los botones en una cuadrícula de colores.|  
|`m_nHorzOffset`|Un entero que es el desplazamiento horizontal al centro del botón de color.  Este valor es significativo si el botón texto o una imagen además del color.|  
|`m_nNumColumns`|Un entero que es el número de columnas en una cuadrícula de control de la barra de color de colores.|  
|`m_nNumColumnsVert`|Un entero que es el número de columnas de una cuadrícula vertical orientada de colores.|  
|`m_nNumRowsHorz`|Un entero que es el número de columnas de una cuadrícula horizontal orientada de colores.|  
|`m_nRowHeight`|Un entero que es el alto de una fila de botones en una cuadrícula de colores.|  
|`m_nVertMargin`|Un entero que es el margen vertical entre los botones en una cuadrícula de colores.|  
|`m_nVertOffset`|Un entero que es el desplazamiento vertical al centro del botón de color.  Este valor es significativo si el botón texto o una imagen además del color.|  
|`m_Palette`|[CPalette](../../mfc/reference/cpalette-class.md) de colores que se utilizan en el control de la barra de color.|  
|`m_pParentBtn`|Un puntero a un objeto de [CMFCColorButton](../../mfc/reference/cmfccolorbutton-class.md) que es el elemento primario de botón actual.  Este valor es significativo si el botón de color está en una jerarquía de controles de la barra de herramientas o está en un control de cuadrícula de la propiedad color.|  
|`m_pParentRibbonBtn`|Un puntero a un objeto de [CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md) que está en la cinta de opciones y es el botón primario del botón actual.  Este valor es significativo si el botón de color está en una jerarquía de controles de la barra de herramientas o está en un control de cuadrícula de la propiedad color.|  
|`m_pWndPropList`|Un puntero a un objeto de [CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md) .|  
|`m_strAutoColor`|[CString](../../atl-mfc-shared/reference/cstringt-class.md) que es el texto que se muestra en el botón de **Automático** .  Para obtener más información, vea [CMFCColorBar::EnableAutomaticButton](../Topic/CMFCColorBar::EnableAutomaticButton.md).|  
|`m_strDocColors`|[CString](../../atl-mfc-shared/reference/cstringt-class.md) que es el texto que se muestra en el botón de los colores del documento.  Para obtener más información, vea [CMFCColorBar::SetDocumentColors](../Topic/CMFCColorBar::SetDocumentColors.md).|  
|`m_strOtherColor`|[CString](../../atl-mfc-shared/reference/cstringt-class.md) que es el texto que se muestra en *el otro* botón.  Para obtener más información, vea [CMFCColorBar::EnableOtherButton](../Topic/CMFCColorBar::EnableOtherButton.md).|  
  
## Comentarios  
 Normalmente, no se crea un objeto de `CMFCColorBar` directamente.  En su lugar, [CMFCColorMenuButton Class](../../mfc/reference/cmfccolormenubutton-class.md) \(utilizado en menús y barras de herramientas\) o [CMFCColorButton Class](../../mfc/reference/cmfccolorbutton-class.md) crea el objeto de `CMFCColorBar` .  
  
 La clase de `CMFCColorBar` proporciona la funcionalidad siguiente:  
  
-   Incluye automáticamente a la lista de colores del documento.  
  
-   Guarda y restaura su estado, así como el estado del documento.  
  
-   Administra el botón “automático”.  
  
-   Utiliza el control de [CMFCColorPickerCtrl Class](../../mfc/reference/cmfccolorpickerctrl-class.md) para seleccionar un color personalizado.  
  
-   Admite “rasgan” el estado \(si se crea utilizando [CMFCColorMenuButton Class](../../mfc/reference/cmfccolormenubutton-class.md)\).  
  
 Para incorporar la funcionalidad de `CMFCColorBar` en su aplicación:  
  
1.  Crear un botón de menú regular y asígnele un id., por ejemplo ID\_CHAR\_COLOR.  
  
2.  En la clase de ventana de marco, invalide el método de [CFrameWndEx::OnShowPopupMenu](../Topic/CFrameWndEx::OnShowPopupMenu.md) y reemplace el botón de menú normal con un objeto de [CMFCColorMenuButton Class](../../mfc/reference/cmfccolormenubutton-class.md) \(llamando a [CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md)\).  
  
3.  Establezca todos los estilos y habilitar o deshabilitar las características del objeto de `CMFCColorBar` durante la creación de [CMFCColorMenuButton Class](../../mfc/reference/cmfccolormenubutton-class.md) .  El objeto de `CMFCColorMenuButton` crea dinámicamente el objeto de `CMFCColorBar` después de que el marco de trabajo llame al método de `CreatePopupMenu` .  
  
 Cuando el usuario hace clic en un botón de control de la barra de color, el marco de trabajo usa la macro de `ON_COMMAND` para notificar al elemento primario del control de barra de color.  En la macro, el parámetro id. de comando es el valor que asignó al botón de control de la barra de color en el paso 1 \(ID\_CHAR\_COLOR en este ejemplo\).  Para obtener más información, vea clases de [CMFCColorMenuButton Class](../../mfc/reference/cmfccolormenubutton-class.md), de [CMFCColorButton Class](../../mfc/reference/cmfccolorbutton-class.md), de [CMFCColorPickerCtrl Class](../../mfc/reference/cmfccolorpickerctrl-class.md), de [CFrameWndEx Class](../../mfc/reference/cframewndex-class.md), y de [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md) .  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo configurar una barra de color mediante varios métodos en la clase de `CMFCColorBar` .  Los métodos establecen los márgenes horizontales y verticales, permiten el otro botón, crea una ventana de control de la barra de color, y establece el color seleccionado actualmente.  Este ejemplo forma parte de [nuevo ejemplo de Controles](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls#1](../../mfc/reference/codesnippet/CPP/cmfccolorbar-class_1.h)]  
[!code-cpp[NVC_MFC_NewControls#2](../../mfc/reference/codesnippet/CPP/cmfccolorbar-class_2.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)  
  
 [CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)  
  
## Requisitos  
 **encabezado:** afxcolorbar.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)