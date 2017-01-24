---
title: "CMFCColorButton Class | Microsoft Docs"
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
  - "CMFCColorButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCColorButton class"
  - "CMFCColorButton::m_bAltColorDlg data member"
  - "CMFCColorButton::m_bAutoSetFocus data member"
  - "CMFCColorButton::m_Color data member"
  - "CMFCColorButton::m_ColorAutomatic data member"
  - "CMFCColorButton::m_lstDocColors data member"
  - "CMFCColorButton::m_nColumns data member"
  - "CMFCColorButton::m_pPalette data member"
  - "CMFCColorButton::m_pPopup data member"
  - "CMFCColorButton::m_strAutoColorText data member"
  - "CMFCColorButton::m_strDocColorsText data member"
  - "CMFCColorButton::m_strOtherText data member"
ms.assetid: 9fdf34ae-4cc5-4c5e-9d89-1c50e8a73699
caps.latest.revision: 34
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCColorButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCColorButton` y las clases de [CMFCColorBar Class](../../mfc/reference/cmfccolorbar-class.md) se utilizan conjuntamente para implementar un control de selector de color.  
  
## Sintaxis  
  
```  
class CMFCColorButton : public CMFCButton  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCColorButton::CMFCColorButton](../Topic/CMFCColorButton::CMFCColorButton.md)|Crea un nuevo objeto `CMFCColorButton`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCColorButton::EnableAutomaticButton](../Topic/CMFCColorButton::EnableAutomaticButton.md)|Habilita y deshabilita un botón “automático” que se coloque sobre los botones de color regulares.  \(El botón automático de sistema estándar se etiqueta **Automático**.\)|  
|[CMFCColorButton::EnableOtherButton](../Topic/CMFCColorButton::EnableOtherButton.md)|Habilita y deshabilita “other” botón que se coloque debajo de los botones de color regulares.  \(El sistema estándar de El “other” botón se etiqueta **más colores…**.\)|  
|[CMFCColorButton::GetAutomaticColor](../Topic/CMFCColorButton::GetAutomaticColor.md)|Recupera el color automático actual.|  
|[CMFCColorButton::GetColor](../Topic/CMFCColorButton::GetColor.md)|Recupera el color de un botón.|  
|[CMFCColorButton::SetColor](../Topic/CMFCColorButton::SetColor.md)|Establece el color de un botón.|  
|[CMFCColorButton::SetColorName](../Topic/CMFCColorButton::SetColorName.md)|Establece un nombre de color.|  
|[CMFCColorButton::SetColumnsNumber](../Topic/CMFCColorButton::SetColumnsNumber.md)|Establece el número de columnas del cuadro de diálogo selector de colores.|  
|[CMFCColorButton::SetDocumentColors](../Topic/CMFCColorButton::SetDocumentColors.md)|Especifica una lista de colores documento\-específicos que aparecen en el cuadro de diálogo selector de colores.|  
|[CMFCColorButton::SetPalette](../Topic/CMFCColorButton::SetPalette.md)|Especifica una paleta colores estándar de la pantalla.|  
|[CMFCColorButton::SizeToContent](../Topic/CMFCColorButton::SizeToContent.md)|Cambia el tamaño del control de botón, dependiendo de su texto y tamaño de la imagen.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCColorButton::IsDrawXPTheme](../Topic/CMFCColorButton::IsDrawXPTheme.md)|Indica si el botón de color actual se muestra en el estilo visual de Windows XP.|  
|[CMFCColorButton::OnDraw](../Topic/CMFCColorButton::OnDraw.md)|Llamado por el marco para mostrar una imagen del botón.|  
|[CMFCColorButton::OnDrawBorder](../Topic/CMFCColorButton::OnDrawBorder.md)|Llamado por el marco para mostrar el borde del botón.|  
|[CMFCColorButton::OnDrawFocusRect](../Topic/CMFCColorButton::OnDrawFocusRect.md)|Llamado por el marco para mostrar un rectángulo de foco cuando el botón tiene el foco.|  
|[CMFCColorButton::OnShowColorPopup](../Topic/CMFCColorButton::OnShowColorPopup.md)|Llamado por el marco cuando el cuadro de diálogo selector de colores se va a mostrar.|  
|[CMFCColorButton::RebuildPalette](../Topic/CMFCColorButton::RebuildPalette.md)|Inicializa el miembro de datos protegido `m_pPalette` a la tabla especificada o a la paleta predeterminada del sistema.|  
|[CMFCColorButton::UpdateColor](../Topic/CMFCColorButton::UpdateColor.md)|Llamado por el marco cuando el usuario seleccione un color de la paleta del cuadro de diálogo selector de colores.|  
  
### miembros de datos  
  
|Name|Descripción|  
|----------|-----------------|  
|`m_bAltColorDlg`|Valor booleano.  Si `TRUE`, el marco muestra el cuadro de diálogo color de [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) cuando se hace clic en *otro* botón, o si `FALSE`, el cuadro de diálogo del color del sistema.  El valor predeterminado es `TRUE`.  Para obtener más información, vea [CMFCColorButton::EnableOtherButton](../Topic/CMFCColorButton::EnableOtherButton.md).|  
|`m_bAutoSetFocus`|Valor booleano.  Si `TRUE`, el marco establece el foco en el menú de color cuando se muestra el menú, o si `FALSE`, no cambia el foco.  El valor predeterminado es `TRUE`.|  
|[CMFCColorButton::m\_bEnabledInCustomizeMode](../Topic/CMFCColorButton::m_bEnabledInCustomizeMode.md)|Indica si se habilita el modo de personalización para el botón de color.|  
|`m_Color`|un valor de [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) .  Contiene el color seleccionado actualmente.|  
|`m_ColorAutomatic`|un valor de [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) .  Contiene el color predeterminado actualmente seleccionado.|  
|`m_Colors`|[CArray](../../mfc/reference/carray-class.md) de los valores de [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) .  Contiene los colores disponibles actualmente.|  
|`m_lstDocColors`|[CList](../../mfc/reference/clist-class.md) de los valores de [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) .  Contiene los colores del documento actual.|  
|`m_nColumns`|Entero.  Contiene el número de columnas para mostrar en la cuadrícula de colores en un menú de selección de color.|  
|`m_pPalette`|un puntero a [CPalette](../../mfc/reference/cpalette-class.md).  Contiene los colores disponibles en el menú de selección actual en color.|  
|`m_pPopup`|un puntero a un objeto de [CMFCColorPopupMenu Class](../../mfc/reference/cmfccolorpopupmenu-class.md) .  El menú de selección de color se muestra al hacer clic en el botón de color.|  
|`m_strAutoColorText`|Una cadena.  La etiqueta del botón “automático” en un menú de selección de color.|  
|`m_strDocColorsText`|Una cadena.  La etiqueta del botón en un menú de selección de color que muestra los colores del documento.|  
|`m_strOtherText`|Una cadena.  La etiqueta de “other” en un menú de selección de color.|  
  
## Comentarios  
 De forma predeterminada, la clase de `CMFCColorButton` se comporta como un botón de comando que abre un cuadro de diálogo selector de colores.  El cuadro de diálogo selector de colores contiene una matriz de pequeños botones de color y “other” botón que muestra un selector de colores personalizados.  \(El sistema estándar de El “other” botón se etiqueta **más colores…**.\) Cuando un usuario selecciona un color nuevo, el objeto de `CMFCColorButton` refleja el cambio y muestra el color seleccionado.  
  
 Cree un control de botón en color directamente en el código, o mediante la herramienta de **ClassWizard** y una plantilla de cuadro de diálogo.  Si crea un control de botón en color directamente, agregue una variable de `CMFCColorButton` a la aplicación, y llame al constructor y los métodos de `Create` del objeto de `CMFCColorButton` .  Si utiliza **ClassWizard**, agregue una variable de `CButton` a la aplicación, y después cambie el tipo de la variable de `CButton` a `CMFCColorButton`.  
  
 El cuadro de diálogo selector de colores \([CMFCColorBar Class](../../mfc/reference/cmfccolorbar-class.md)\) se muestra mediante el método de [CMFCColorButton::OnShowColorPopup](../Topic/CMFCColorButton::OnShowColorPopup.md) cuando el marco de trabajo llama al controlador de eventos de `OnLButtonDown` .  El método de [CMFCColorButton::OnShowColorPopup](../Topic/CMFCColorButton::OnShowColorPopup.md) se puede invalidar para admitir la selección de colores personalizada.  
  
 El objeto de `CMFCColorButton` notifica a su elemento primario que color cambia enviándole una notificación de `WM_COMMAND | BN_CLICKED` .  El elemento primario usa el método de [CMFCColorButton::GetColor](../Topic/CMFCColorButton::GetColor.md) para recuperar el color actual.  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo configurar un botón en color mediante varios métodos en la clase de `CMFCColorButton` .  Los métodos establecen el color del botón de color y del número de columnas, y permiten los botones automáticos y otros.  Este ejemplo forma parte de [Ejemplo de demostración de la barra de estado](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_StatusBarDemo#10](../../mfc/reference/codesnippet/CPP/cmfccolorbutton-class_1.h)]  
[!code-cpp[NVC_MFC_StatusBarDemo#11](../../mfc/reference/codesnippet/CPP/cmfccolorbutton-class_2.cpp)]  
  
## Requisitos  
 **encabezado:** afxcolorbutton.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCButton Class](../../mfc/reference/cmfcbutton-class.md)   
 [CMFCColorBar Class](../../mfc/reference/cmfccolorbar-class.md)   
 [CMFCColorButton::OnShowColorPopup](../Topic/CMFCColorButton::OnShowColorPopup.md)   
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)   
 [CPalette Class](../../mfc/reference/cpalette-class.md)   
 [CArray Class](../../mfc/reference/carray-class.md)   
 [CList Class](../../mfc/reference/clist-class.md)   
 [CString](../../atl-mfc-shared/reference/cstringt-class.md)