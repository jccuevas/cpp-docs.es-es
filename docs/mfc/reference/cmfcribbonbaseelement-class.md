---
title: "CMFCRibbonBaseElement Class | Microsoft Docs"
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
  - "CMFCRibbonBaseElement"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonBaseElement class"
ms.assetid: 419ea91b-5062-44cc-b0a3-f87d29566f62
caps.latest.revision: 34
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonBaseElement Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CMFCRibbonBaseElement` es la clase base para todos los elementos que puede agregar a [barra de la cinta de opciones](../../mfc/reference/cmfcribbonbar-class.md).  Los ejemplos de elementos de la cinta de opciones son botones de la cinta de opciones, las casillas de la cinta de opciones, y cuadros combinados de la cinta de opciones.  
  
## Sintaxis  
  
```  
class CMFCRibbonBaseElement : public CObject  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCRibbonBaseElement`|Crea un objeto `CMFCRibbonBaseElement`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonBaseElement::AddToKeyList](../Topic/CMFCRibbonBaseElement::AddToKeyList.md)|Agrega un keytip para el elemento cinta a una matriz de keytips.|  
|[CMFCRibbonBaseElement::AddToListBox](../Topic/CMFCRibbonBaseElement::AddToListBox.md)|Agrega un elemento cinta al cuadro de lista especificado de los comandos de la cinta de opciones.|  
|[CMFCRibbonBaseElement::CanBeAddedToQuickAccessToolBar](../Topic/CMFCRibbonBaseElement::CanBeAddedToQuickAccessToolBar.md)|Indica si el elemento cinta se puede agregar a la barra de herramientas de acceso rápido.|  
|[CMFCRibbonBaseElement::CanBeCompacted](../Topic/CMFCRibbonBaseElement::CanBeCompacted.md)|Indica si el tamaño del elemento cinta puede ser compacto.|  
|[CMFCRibbonBaseElement::CanBeStretched](../Topic/CMFCRibbonBaseElement::CanBeStretched.md)|Indica si el alto del elemento cinta puede aumentar verticalmente el alto de una fila de la cinta de opciones.|  
|[CMFCRibbonBaseElement::CanBeStretchedHorizontally](../Topic/CMFCRibbonBaseElement::CanBeStretchedHorizontally.md)|Indica si el ancho del elemento cinta puede cambiar.|  
|[CMFCRibbonBaseElement::CleanUpSizes](../Topic/CMFCRibbonBaseElement::CleanUpSizes.md)|Limpia los valores de dimensión para el elemento cinta.|  
|[CMFCRibbonBaseElement::ClosePopupMenu](../Topic/CMFCRibbonBaseElement::ClosePopupMenu.md)|Cierre el elemento emergente del elemento cinta.|  
|[CMFCRibbonBaseElement::CopyFrom](../Topic/CMFCRibbonBaseElement::CopyFrom.md)|Copia el estado de `CMFCRibbonBaseElement` especificado al objeto actual.|  
|[CMFCRibbonBaseElement::DestroyCtrl](../Topic/CMFCRibbonBaseElement::DestroyCtrl.md)|Destruye el elemento cinta.|  
|[CMFCRibbonBaseElement::DrawImage](../Topic/CMFCRibbonBaseElement::DrawImage.md)|Dibuja la imagen para el elemento cinta.|  
|[CMFCRibbonBaseElement::Find](../Topic/CMFCRibbonBaseElement::Find.md)|Devuelve el puntero especificado al elemento cinta si señala al objeto actual.|  
|[CMFCRibbonBaseElement::FindByData](../Topic/CMFCRibbonBaseElement::FindByData.md)|Recupera un puntero al elemento cinta si contiene los datos especificados.|  
|[CMFCRibbonBaseElement::FindByID](../Topic/CMFCRibbonBaseElement::FindByID.md)|Recupera un puntero al elemento cinta si ese elemento se identifica mediante el identificador especificado de comando|  
|[CMFCRibbonBaseElement::FindByOriginal](../Topic/CMFCRibbonBaseElement::FindByOriginal.md)|Recupera un puntero al elemento cinta si las coincidencias originales del elemento cinta el elemento especificado de la cinta de opciones.|  
|[CMFCRibbonBaseElement::GetCompactSize](../Topic/CMFCRibbonBaseElement::GetCompactSize.md)|Devuelve el tamaño compacto de elemento cinta.|  
|[CMFCRibbonBaseElement::GetData](../Topic/CMFCRibbonBaseElement::GetData.md)|Recupera los datos definidos por el usuario asociados al elemento cinta.|  
|[CMFCRibbonBaseElement::GetDescription](../Topic/CMFCRibbonBaseElement::GetDescription.md)|Devuelve la descripción del elemento cinta.|  
|[CMFCRibbonBaseElement::GetDroppedDown](../Topic/CMFCRibbonBaseElement::GetDroppedDown.md)|Recupera un puntero al elemento cinta si el elemento emergente se quita a continuación.|  
|[CMFCRibbonBaseElement::GetElements](../Topic/CMFCRibbonBaseElement::GetElements.md)|Agrega el elemento actual de la cinta de opciones en la matriz especificada.|  
|[CMFCRibbonBaseElement::GetElementsByID](../Topic/CMFCRibbonBaseElement::GetElementsByID.md)|Agrega el elemento actual de la cinta de opciones en la matriz especificada si el elemento actual de la cinta de opciones contiene el identificador especificado de comando|  
|[CMFCRibbonBaseElement::GetHighlighted](../Topic/CMFCRibbonBaseElement::GetHighlighted.md)|Recupera un puntero al elemento cinta si es resaltado.|  
|[CMFCRibbonBaseElement::GetID](../Topic/CMFCRibbonBaseElement::GetID.md)|Devuelve el identificador del elemento cinta.|  
|[CMFCRibbonBaseElement::GetImageSize](../Topic/CMFCRibbonBaseElement::GetImageSize.md)|Devuelve el tamaño de la imagen del elemento cinta.|  
|[CMFCRibbonBaseElement::GetIntermediateSize](../Topic/CMFCRibbonBaseElement::GetIntermediateSize.md)|Devuelve el tamaño del elemento cinta en su estado intermedia.|  
|[CMFCRibbonBaseElement::GetKeys](../Topic/CMFCRibbonBaseElement::GetKeys.md)|Devuelve el keytip asociado con el elemento cinta.|  
|[CMFCRibbonBaseElement::GetKeyTipRect](../Topic/CMFCRibbonBaseElement::GetKeyTipRect.md)|Recupera el rectángulo de selección de keytip para el elemento cinta.|  
|[CMFCRibbonBaseElement::GetKeyTipSize](../Topic/CMFCRibbonBaseElement::GetKeyTipSize.md)|Recupera el tamaño del texto de keytip.|  
|[CMFCRibbonBaseElement::GetLocationInGroup](../Topic/CMFCRibbonBaseElement::GetLocationInGroup.md)|Indica la ubicación de la presentación del elemento cinta en un grupo de la cinta de opciones.|  
|[CMFCRibbonBaseElement::GetMenuKeys](../Topic/CMFCRibbonBaseElement::GetMenuKeys.md)|Devuelve los keytips asociados a un botón.|  
|[CMFCRibbonBaseElement::GetNotifyID](../Topic/CMFCRibbonBaseElement::GetNotifyID.md)|Recupera el id. de comando de notificación para el elemento cinta.|  
|[CMFCRibbonBaseElement::GetOriginal](../Topic/CMFCRibbonBaseElement::GetOriginal.md)|Recupera el elemento original de la cinta de opciones.|  
|[CMFCRibbonBaseElement::GetParentCategory](../Topic/CMFCRibbonBaseElement::GetParentCategory.md)|Recupera la categoría de la cinta de opciones para el elemento cinta.|  
|[CMFCRibbonBaseElement::GetParentPanel](../Topic/CMFCRibbonBaseElement::GetParentPanel.md)|Recupera el panel de la cinta que contiene el elemento cinta.|  
|[CMFCRibbonBaseElement::GetParentRibbonBar](../Topic/CMFCRibbonBaseElement::GetParentRibbonBar.md)|Recupera la barra primaria de la cinta de opciones para el elemento cinta.|  
|[CMFCRibbonBaseElement::GetParentWnd](../Topic/CMFCRibbonBaseElement::GetParentWnd.md)|Recupera la ventana primaria para el elemento cinta.|  
|[CMFCRibbonBaseElement::GetPressed](../Topic/CMFCRibbonBaseElement::GetPressed.md)|Recupera un puntero al elemento cinta si el usuario se presiona actualmente.|  
|[CMFCRibbonBaseElement::GetQuickAccessToolBarID](../Topic/CMFCRibbonBaseElement::GetQuickAccessToolBarID.md)|Recupera el identificador del elemento cinta cuando se encuentra en la barra de herramientas de acceso rápido.|  
|[CMFCRibbonBaseElement::GetRect](../Topic/CMFCRibbonBaseElement::GetRect.md)|Devuelve el rectángulo delimitador del elemento cinta.|  
|[CMFCRibbonBaseElement::GetRegularSize](../Topic/CMFCRibbonBaseElement::GetRegularSize.md)|Devuelve el tamaño normal del elemento cinta.|  
|[CMFCRibbonBaseElement::GetSize](../Topic/CMFCRibbonBaseElement::GetSize.md)|Devuelve el tamaño actual del elemento cinta.|  
|[CMFCRibbonBaseElement::GetText](../Topic/CMFCRibbonBaseElement::GetText.md)|Devuelve el texto asociado al elemento cinta.|  
|[CMFCRibbonBaseElement::GetToolTipText](../Topic/CMFCRibbonBaseElement::GetToolTipText.md)|Devuelve el texto de información sobre herramientas del elemento cinta.|  
|[CMFCRibbonBaseElement::GetTopLevelRibbonBar](../Topic/CMFCRibbonBaseElement::GetTopLevelRibbonBar.md)|Recupera la barra de la cinta de opciones de nivel superior para el elemento cinta.|  
|[CMFCRibbonBaseElement::HasCompactMode](../Topic/CMFCRibbonBaseElement::HasCompactMode.md)|Especifica si el elemento cinta tiene un modo compacto.|  
|[CMFCRibbonBaseElement::HasFocus](../Topic/CMFCRibbonBaseElement::HasFocus.md)|Indica si el elemento primario tiene el foco de teclado.|  
|[CMFCRibbonBaseElement::HasIntermediateMode](../Topic/CMFCRibbonBaseElement::HasIntermediateMode.md)|Especifica si el elemento cinta tiene un modo intermedio.|  
|[CMFCRibbonBaseElement::HasLargeMode](../Topic/CMFCRibbonBaseElement::HasLargeMode.md)|Especifica si el elemento cinta tiene un modo grande.|  
|[CMFCRibbonBaseElement::HasMenu](../Topic/CMFCRibbonBaseElement::HasMenu.md)|Indica si el elemento cinta tiene un menú.|  
|[CMFCRibbonBaseElement::HitTest](../Topic/CMFCRibbonBaseElement::HitTest.md)|Recupera un puntero al elemento cinta si el punto especificado se encuentra en él.|  
|[CMFCRibbonBaseElement::IsAlignByColumn](../Topic/CMFCRibbonBaseElement::IsAlignByColumn.md)|Indica si el elemento cinta está alineado verticalmente con otros elementos de cinta de opciones.|  
|[CMFCRibbonBaseElement::IsAlwaysLargeImage](../Topic/CMFCRibbonBaseElement::IsAlwaysLargeImage.md)|Indica si el tamaño de la imagen del elemento cinta siempre es grande.|  
|[CMFCRibbonBaseElement::IsAutoRepeatMode](../Topic/CMFCRibbonBaseElement::IsAutoRepeatMode.md)|Indica si el elemento cinta está en modo de repetición automática.|  
|[CMFCRibbonBaseElement::IsChecked](../Topic/CMFCRibbonBaseElement::IsChecked.md)|Especifica si el elemento cinta está activado.|  
|[CMFCRibbonBaseElement::IsCompactMode](../Topic/CMFCRibbonBaseElement::IsCompactMode.md)|Especifica si el elemento cinta está en un modo compacto.|  
|[CMFCRibbonBaseElement::IsDefaultMenuLook](../Topic/CMFCRibbonBaseElement::IsDefaultMenuLook.md)||  
|[CMFCRibbonBaseElement::IsDisabled](../Topic/CMFCRibbonBaseElement::IsDisabled.md)|Especifica si el elemento cinta está deshabilitado.|  
|[CMFCRibbonBaseElement::IsDroppedDown](../Topic/CMFCRibbonBaseElement::IsDroppedDown.md)|Determina si el elemento cinta muestra un menú emergente y se divide a continuación.|  
|[CMFCRibbonBaseElement::IsFocused](../Topic/CMFCRibbonBaseElement::IsFocused.md)|Especifica si el elemento cinta tiene el foco.|  
|[CMFCRibbonBaseElement::IsGalleryIcon](../Topic/CMFCRibbonBaseElement::IsGalleryIcon.md)|Indica si el elemento cinta está contenido en una galería de la cinta de opciones.|  
|[CMFCRibbonBaseElement::IsHighlighted](../Topic/CMFCRibbonBaseElement::IsHighlighted.md)|Especifica si el elemento cinta aparecerá resaltada.|  
|[CMFCRibbonBaseElement::IsIntermediateMode](../Topic/CMFCRibbonBaseElement::IsIntermediateMode.md)|Indica si la imagen actual para el elemento cinta es tamaño intermedio.|  
|[CMFCRibbonBaseElement::IsLargeMode](../Topic/CMFCRibbonBaseElement::IsLargeMode.md)|Indica si la imagen actual para el elemento cinta es de gran tamaño.|  
|[CMFCRibbonBaseElement::IsMenuMode](../Topic/CMFCRibbonBaseElement::IsMenuMode.md)|Indica si el elemento cinta está contenido en un menú.|  
|[CMFCRibbonBaseElement::IsPressed](../Topic/CMFCRibbonBaseElement::IsPressed.md)|Indica si el usuario ha hecho clic en el elemento cinta.|  
|[CMFCRibbonBaseElement::IsQATMode](../Topic/CMFCRibbonBaseElement::IsQATMode.md)|Indica si el elemento cinta está contenido en la barra de herramientas de acceso rápido.|  
|[CMFCRibbonBaseElement::IsSeparator](../Topic/CMFCRibbonBaseElement::IsSeparator.md)|Indica si el elemento cinta es un separador de la pantalla.|  
|[CMFCRibbonBaseElement::IsShowGroupBorder](../Topic/CMFCRibbonBaseElement::IsShowGroupBorder.md)|Indica si el elemento cinta está contenido en un grupo que muestra un borde común.|  
|[CMFCRibbonBaseElement::IsShowTooltipOnBottom](../Topic/CMFCRibbonBaseElement::IsShowTooltipOnBottom.md)|Indica si la información sobre herramientas se muestra bajo el elemento cinta.|  
|[CMFCRibbonBaseElement::IsTabStop](../Topic/CMFCRibbonBaseElement::IsTabStop.md)|Indica si el elemento cinta puede seleccionar con el teclado.|  
|[CMFCRibbonBaseElement::IsTextAlwaysOnRight](../Topic/CMFCRibbonBaseElement::IsTextAlwaysOnRight.md)|Indica si el texto para el elemento cinta aparece a la derecha.|  
|[CMFCRibbonBaseElement::IsVisible](../Topic/CMFCRibbonBaseElement::IsVisible.md)|Indica si el elemento cinta se muestra actualmente.|  
|[CMFCRibbonBaseElement::IsWholeRowHeight](../Topic/CMFCRibbonBaseElement::IsWholeRowHeight.md)|Indica si el heigth de presentación del elemento cinta es igual que el alto de la pantalla del panel de la cinta que lo contiene.|  
|[CMFCRibbonBaseElement::NotifyCommand](../Topic/CMFCRibbonBaseElement::NotifyCommand.md)|Envía una notificación de comando a la ventana principal del elemento cinta.|  
|[CMFCRibbonBaseElement::NotifyHighlightListItem](../Topic/CMFCRibbonBaseElement::NotifyHighlightListItem.md)|Notifica a la ventana primaria de la barra de la cinta de opciones a un usuario se resalta el elemento cinta que se encuentra en una lista.|  
|[CMFCRibbonBaseElement::OnAddToQAToolbar](../Topic/CMFCRibbonBaseElement::OnAddToQAToolbar.md)|Agrega el elemento cinta a la barra de herramientas especificada de acceso rápido.|  
|[CMFCRibbonBaseElement::OnAfterChangeRect](../Topic/CMFCRibbonBaseElement::OnAfterChangeRect.md)|Actualiza la información sobre herramientas para el elemento cinta.|  
|[CMFCRibbonBaseElement::OnAutoRepeat](../Topic/CMFCRibbonBaseElement::OnAutoRepeat.md)|Actualiza el elemento cinta en respuesta a los datos proporcionados por el usuario continuo.|  
|[CMFCRibbonBaseElement::OnCalcTextSize](../Topic/CMFCRibbonBaseElement::OnCalcTextSize.md)|Calcula el tamaño del texto para el elemento cinta.|  
|[CMFCRibbonBaseElement::OnChangeMenuHighlight](../Topic/CMFCRibbonBaseElement::OnChangeMenuHighlight.md)|Llamado por el marco cuando el resaltado de un elemento cinta que se encuentra en un menú.|  
|[CMFCRibbonBaseElement::OnDraw](../Topic/CMFCRibbonBaseElement::OnDraw.md)|Llamado por el marco para dibujar el elemento cinta.|  
|[CMFCRibbonBaseElement::OnDrawKeyTip](../Topic/CMFCRibbonBaseElement::OnDrawKeyTip.md)|Llamado por el marco para dibujar el keytip para el elemento cinta.|  
|[CMFCRibbonBaseElement::OnDrawMenuImage](../Topic/CMFCRibbonBaseElement::OnDrawMenuImage.md)|Llamado por el marco cuando la imagen del menú para el elemento cinta se dibuja.|  
|[CMFCRibbonBaseElement::OnDrawOnList](../Topic/CMFCRibbonBaseElement::OnDrawOnList.md)|Llamado por el marco para dibujar el elemento cinta en un cuadro de lista de comandos.|  
|[CMFCRibbonBaseElement::OnKey](../Topic/CMFCRibbonBaseElement::OnKey.md)|Llamado por el marco cuando el usuario presiona un keytip y el elemento cinta tiene el foco.|  
|[CMFCRibbonBaseElement::OnMenuKey](../Topic/CMFCRibbonBaseElement::OnMenuKey.md)||  
|[CMFCRibbonBaseElement::OnRTLChanged](../Topic/CMFCRibbonBaseElement::OnRTLChanged.md)|Llamado por el marco cuando el diseño cambia la dirección.|  
|[CMFCRibbonBaseElement::OnShow](../Topic/CMFCRibbonBaseElement::OnShow.md)|Llamado por el marco para mostrar u ocultar el elemento cinta.|  
|[CMFCRibbonBaseElement::OnShowPopupMenu](../Topic/CMFCRibbonBaseElement::OnShowPopupMenu.md)|Llamado por el marco cuando el elemento cinta va a mostrar un menú emergente.|  
|[CMFCRibbonBaseElement::PostMenuCommand](../Topic/CMFCRibbonBaseElement::PostMenuCommand.md)||  
|[CMFCRibbonBaseElement::Redraw](../Topic/CMFCRibbonBaseElement::Redraw.md)|Actualiza la presentación para el elemento cinta.|  
|[CMFCRibbonBaseElement::SetACCData](../Topic/CMFCRibbonBaseElement::SetACCData.md)|Establece los datos de accesibilidad para el elemento cinta.|  
|[CMFCRibbonBaseElement::SetCompactMode](../Topic/CMFCRibbonBaseElement::SetCompactMode.md)|Establece el tamaño de presentación para el elemento cinta.|  
|[CMFCRibbonBaseElement::SetData](../Topic/CMFCRibbonBaseElement::SetData.md)|Asocia un elemento de datos al elemento cinta.|  
|[CMFCRibbonBaseElement::SetDefaultMenuLook](../Topic/CMFCRibbonBaseElement::SetDefaultMenuLook.md)||  
|[CMFCRibbonBaseElement::SetDescription](../Topic/CMFCRibbonBaseElement::SetDescription.md)|Establece la descripción para el elemento cinta.|  
|[CMFCRibbonBaseElement::SetID](../Topic/CMFCRibbonBaseElement::SetID.md)|Establece el identificador del elemento cinta.|  
|[CMFCRibbonBaseElement::SetInitialMode](../Topic/CMFCRibbonBaseElement::SetInitialMode.md)|Establece el tamaño inicial de presentación para el elemento cinta.|  
|[CMFCRibbonBaseElement::SetKeys](../Topic/CMFCRibbonBaseElement::SetKeys.md)|Establece un keytip para el elemento cinta.|  
|[CMFCRibbonBaseElement::SetOriginal](../Topic/CMFCRibbonBaseElement::SetOriginal.md)|Establece el elemento original de la cinta de opciones para el elemento cinta.|  
|[CMFCRibbonBaseElement::SetParentCategory](../Topic/CMFCRibbonBaseElement::SetParentCategory.md)|Establece la categoría primaria para el elemento cinta.|  
|[CMFCRibbonBaseElement::SetParentMenu](../Topic/CMFCRibbonBaseElement::SetParentMenu.md)|Establece el contenedor de menú primario para el elemento cinta.|  
|[CMFCRibbonBaseElement::SetParentRibbonBar](../Topic/CMFCRibbonBaseElement::SetParentRibbonBar.md)|Establece la barra primaria de la cinta de opciones para el elemento cinta.|  
|[CMFCRibbonBaseElement::SetRect](../Topic/CMFCRibbonBaseElement::SetRect.md)|Establece las dimensiones que se muestra fot el rectángulo para el elemento cinta.|  
|[CMFCRibbonBaseElement::SetText](../Topic/CMFCRibbonBaseElement::SetText.md)|Establece el texto para el elemento cinta.|  
|[CMFCRibbonBaseElement::SetTextAlwaysOnRight](../Topic/CMFCRibbonBaseElement::SetTextAlwaysOnRight.md)|Establece el texto del elemento cinta muestra a la derecha.|  
|[CMFCRibbonBaseElement::SetToolTipText](../Topic/CMFCRibbonBaseElement::SetToolTipText.md)|Establece el texto de información sobre herramientas para el elemento cinta.|  
|[CMFCRibbonBaseElement::SetVisible](../Topic/CMFCRibbonBaseElement::SetVisible.md)|Establece el estado de visibilidad del elemento cinta.|  
|[CMFCRibbonBaseElement::StretchHorizontally](../Topic/CMFCRibbonBaseElement::StretchHorizontally.md)|Expande el ancho del elemento cinta.|  
|[CMFCRibbonBaseElement::StretchToWholeRow](../Topic/CMFCRibbonBaseElement::StretchToWholeRow.md)|Cambia el alto de la presentación de un elemento de la cinta de opciones al alto de fila especificado.|  
|[CMFCRibbonBaseElement::UpdateTooltipInfo](../Topic/CMFCRibbonBaseElement::UpdateTooltipInfo.md)|Actualiza el texto de información sobre herramientas mediante el recurso de comando para el elemento cinta.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonBaseElement::OnProcessKey](../Topic/CMFCRibbonBaseElement::OnProcessKey.md)|Llamado por el marco cuando el usuario presiona una tecla de método abreviado.|  
|[CMFCRibbonBaseElement::OnSetFocus](../Topic/CMFCRibbonBaseElement::OnSetFocus.md)|Llamado por el marco cuando un elemento cinta recibe o pierde el foco de entrada.|  
  
## Comentarios  
 La clase de `CMFCRibbonBaseElement` define las propiedades que son comunes a todos los elementos de la cinta de opciones que incluyen id. del comando, el etiqueta de texto, el texto de información sobre herramientas, la descripción del elemento, y estado \(que puede ser detallada, ser resaltada, ser presionado, deshabilitar, comprobarse, o se interrumpe a continuación\).  
  
 El tamaño de la imagen de un elemento cinta lo define el miembro de `RibbonImageType` , que puede ser uno de los siguientes valores:  
  
-   `RibbonImageLarge`  
  
-   `RibbonImageSmall`  
  
 Dependiendo de su tamaño, un elemento cinta muestra una imagen pequeña o grande.  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo utilizar varios métodos en la clase de `CMFCRibbonBaseElement` .  El ejemplo muestra cómo obtener un objeto de `CMFCRibbonBaseElement` de una clase de `CMFCRibbonStatusBar` , establece la descripción para el elemento cinta, establece el texto, establece un keytip, y establece el texto de información sobre herramientas para el elemento cinta.  Este fragmento de código es parte de [Ejemplo de cliente de dibujo](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DrawClient#8](../../mfc/reference/codesnippet/CPP/cmfcribbonbaseelement-class_1.cpp)]  
[!code-cpp[NVC_MFC_DrawClient#9](../../mfc/reference/codesnippet/CPP/cmfcribbonbaseelement-class_2.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
## Requisitos  
 **encabezado:** afxbaseribbonelement.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)