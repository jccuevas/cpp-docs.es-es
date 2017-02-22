---
title: "CMFCToolBarButton Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCToolBarButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolBarButton class"
ms.assetid: 8a6ecffb-86b0-4f5c-8211-a9146b463efd
caps.latest.revision: 34
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 36
---
# CMFCToolBarButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona funcionalidad del botón en las barras de herramientas.  
  
## Sintaxis  
  
```  
class CMFCToolBarButton : public CObject  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCToolBarButton::CMFCToolBarButton](../Topic/CMFCToolBarButton::CMFCToolBarButton.md)|Las construcciones e inicializan un objeto de `CMFCToolBarButton` .|  
|`CMFCToolBarButton::~CMFCToolBarButton`|Un destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCToolBarButton::CanBeDropped](../Topic/CMFCToolBarButton::CanBeDropped.md)|Especifica si un usuario puede colocar un botón de una barra de herramientas o menú durante la personalización.|  
|[CMFCToolBarButton::CanBeStored](../Topic/CMFCToolBarButton::CanBeStored.md)|Especifica si el botón puede almacenar.|  
|[CMFCToolBarButton::CanBeStretched](../Topic/CMFCToolBarButton::CanBeStretched.md)|Especifica si un usuario puede ajustar el botón durante la personalización.|  
|[CMFCToolBarButton::CompareWith](../Topic/CMFCToolBarButton::CompareWith.md)|compara esta instancia con el objeto proporcionado de `CMFCToolBarButton` .|  
|[CMFCToolBarButton::CopyFrom](../Topic/CMFCToolBarButton::CopyFrom.md)|Copia las propiedades de otro botón de la barra de herramientas para el botón actual.|  
|[CMFCToolBarButton::CreateFromOleData](../Topic/CMFCToolBarButton::CreateFromOleData.md)|Crea un objeto de `CMFCToolBarButton` del objeto proporcionado de `COleDataObject` .|  
|`CMFCToolBarButton::CreateObject`|Utiliza el marco para crear una instancia dinámica de este tipo de clase.|  
|[CMFCToolBarButton::EnableWindow](../Topic/CMFCToolBarButton::EnableWindow.md)|Habilita o deshabilita la entrada del mouse y del teclado.|  
|[CMFCToolBarButton::ExportToMenuButton](../Topic/CMFCToolBarButton::ExportToMenuButton.md)|Copia el texto del botón de la barra de herramientas a un menú.|  
|[CMFCToolBarButton::GetClipboardFormat](../Topic/CMFCToolBarButton::GetClipboardFormat.md)|Recupera el formato global del portapapeles para la aplicación.|  
|[CMFCToolBarButton::GetHwnd](../Topic/CMFCToolBarButton::GetHwnd.md)|Recupera el identificador de ventana que está asociado al botón de la barra de herramientas.|  
|[CMFCToolBarButton::GetImage](../Topic/CMFCToolBarButton::GetImage.md)|Recupera el índice del botón.|  
|[CMFCToolBarButton::GetInvalidateRect](../Topic/CMFCToolBarButton::GetInvalidateRect.md)|Recupera la región del área cliente del botón que debe volver a dibujar.|  
|[CMFCToolBarButton::GetParentWnd](../Topic/CMFCToolBarButton::GetParentWnd.md)|Recupera la ventana primaria del botón.|  
|[CMFCToolBarButton::GetProtectedCommands](../Topic/CMFCToolBarButton::GetProtectedCommands.md)|recupera la lista de comandos que el usuario no puede personalizar.|  
|[CMFCToolBarButton::GetTextSize](../Topic/CMFCToolBarButton::GetTextSize.md)|Recupera el tamaño del texto del botón.|  
|[CMFCToolBarButton::HasFocus](../Topic/CMFCToolBarButton::HasFocus.md)|determina si el botón tiene el foco de entrada actual.|  
|[CMFCToolBarButton::HaveHotBorder](../Topic/CMFCToolBarButton::HaveHotBorder.md)|Determina si un borde del botón de cuando un usuario selecciona el botón.|  
|[CMFCToolBarButton::IsDrawImage](../Topic/CMFCToolBarButton::IsDrawImage.md)|Determina si una imagen se muestra en el botón.|  
|[CMFCToolBarButton::IsDrawText](../Topic/CMFCToolBarButton::IsDrawText.md)|Determina si una etiqueta de texto se muestra en el botón.|  
|[CMFCToolBarButton::IsDroppedDown](../Topic/CMFCToolBarButton::IsDroppedDown.md)|Determina si el botón muestra un submenú.|  
|[CMFCToolBarButton::IsEditable](../Topic/CMFCToolBarButton::IsEditable.md)|Determina si el botón puede personalizarse.|  
|[CMFCToolBarButton::IsExtraSize](../Topic/CMFCToolBarButton::IsExtraSize.md)|Determina si el botón se puede mostrar con un borde extendido.|  
|[CMFCToolBarButton::IsFirstInGroup](../Topic/CMFCToolBarButton::IsFirstInGroup.md)|determina si el botón está en la primera posición en su grupo de botones.|  
|[CMFCToolBarButton::IsHidden](../Topic/CMFCToolBarButton::IsHidden.md)|Determina si el botón está oculto.|  
|[CMFCToolBarButton::IsHorizontal](../Topic/CMFCToolBarButton::IsHorizontal.md)|Determina si el botón se encuentra en una barra de herramientas horizontal.|  
|[CMFCToolBarButton::IsLastInGroup](../Topic/CMFCToolBarButton::IsLastInGroup.md)|Especifica si el botón está en posición última en su grupo de botones.|  
|[CMFCToolBarButton::IsLocked](../Topic/CMFCToolBarButton::IsLocked.md)|Determina si el botón está en una barra de herramientas \(no\-adaptable\) para.|  
|[CMFCToolBarButton::IsOwnerOf](../Topic/CMFCToolBarButton::IsOwnerOf.md)|Determina si el botón es el propietario del identificador de ventana proporcionado.|  
|[CMFCToolBarButton::IsVisible](../Topic/CMFCToolBarButton::IsVisible.md)|Determina si el botón de la barra de herramientas está visible.|  
|[CMFCToolBarButton::IsWindowVisible](../Topic/CMFCToolBarButton::IsWindowVisible.md)|Determina si el identificador de ventana subyacente del botón está visible.|  
|[CMFCToolBarButton::NotifyCommand](../Topic/CMFCToolBarButton::NotifyCommand.md)|especifica si el botón procesa el mensaje de [WM\_COMMAND](http://msdn.microsoft.com/library/windows/desktop/ms647591) .|  
|[CMFCToolBarButton::OnAddToCustomizePage](../Topic/CMFCToolBarButton::OnAddToCustomizePage.md)|Llamado por el marco cuando el botón se agrega a un cuadro de diálogo de **Personalizar** .|  
|[CMFCToolBarButton::OnBeforeDrag](../Topic/CMFCToolBarButton::OnBeforeDrag.md)|Especifica si el botón pueda arrastrar.|  
|[CMFCToolBarButton::OnBeforeDrop](../Topic/CMFCToolBarButton::OnBeforeDrop.md)|Especifica si un usuario puede quitar el botón en la barra de herramientas de destino.|  
|[CMFCToolBarButton::OnCalculateSize](../Topic/CMFCToolBarButton::OnCalculateSize.md)|Llamado por el marco para calcular el tamaño del botón para el contexto y el estado de vinculación especificados del dispositivo.|  
|[CMFCToolBarButton::OnCancelMode](../Topic/CMFCToolBarButton::OnCancelMode.md)|Llamado por el marco para procesar el mensaje de [WM\_CANCELMODE](http://msdn.microsoft.com/library/windows/desktop/ms632615) .|  
|[CMFCToolBarButton::OnChangeParentWnd](../Topic/CMFCToolBarButton::OnChangeParentWnd.md)|Llamado por el marco cuando el botón se inserta en una nueva barra de herramientas.|  
|[CMFCToolBarButton::OnClick](../Topic/CMFCToolBarButton::OnClick.md)|Llamado por el marco cuando el usuario hace clic en el botón del mouse.|  
|[CMFCToolBarButton::OnClickUp](../Topic/CMFCToolBarButton::OnClickUp.md)|Llamado por el marco cuando el usuario suelta el botón del mouse.|  
|[CMFCToolBarButton::OnContextHelp](../Topic/CMFCToolBarButton::OnContextHelp.md)|Llamado por el marco cuando la barra de herramientas principal controla un mensaje de `WM_HELPHITTEST` .|  
|[CMFCToolBarButton::OnCtlColor](../Topic/CMFCToolBarButton::OnCtlColor.md)|Llamado por el marco cuando la barra de herramientas principal controla un mensaje de `WM_CTLCOLOR` .|  
|[CMFCToolBarButton::OnCustomizeMenu](../Topic/CMFCToolBarButton::OnCustomizeMenu.md)|Permite que el botón modifique el menú proporcionado cuando la aplicación muestra un menú contextual en la barra de herramientas principal.|  
|[CMFCToolBarButton::OnDblClk](../Topic/CMFCToolBarButton::OnDblClk.md)|Llamado por el marco cuando la barra de herramientas principal controla un mensaje de [WM\_LBUTTONDBLCLK](http://msdn.microsoft.com/library/windows/desktop/ms645606) .|  
|[CMFCToolBarButton::OnDraw](../Topic/CMFCToolBarButton::OnDraw.md)|Llamado por el marco para dibujar el botón mediante los estilos y las opciones especificados.|  
|[CMFCToolBarButton::OnDrawOnCustomizeList](../Topic/CMFCToolBarButton::OnDrawOnCustomizeList.md)|Llamado por el marco para dibujar el botón del panel de Commandos del cuadro de diálogo de **Personalizar** .|  
|[CMFCToolBarButton::OnGetCustomToolTipText](../Topic/CMFCToolBarButton::OnGetCustomToolTipText.md)|Llamado por el marco para recuperar el texto de información sobre herramientas personalizado para el botón.|  
|[CMFCToolBarButton::OnGlobalFontsChanged](../Topic/CMFCToolBarButton::OnGlobalFontsChanged.md)|Llamado por el marco cuando la fuente global ha cambiado.|  
|[CMFCToolBarButton::OnMove](../Topic/CMFCToolBarButton::OnMove.md)|Llamado por el marco cuando la barra de herramientas principal se mueve.|  
|[CMFCToolBarButton::OnShow](../Topic/CMFCToolBarButton::OnShow.md)|Llamado por el marco cuando el botón se vuelve visible o invisible.|  
|[CMFCToolBarButton::OnSize](../Topic/CMFCToolBarButton::OnSize.md)|Llamado por el marco cuando la barra de herramientas principal cambia su tamaño o posición y este cambio requiere el botón cambiar el tamaño.|  
|[CMFCToolBarButton::OnToolHitTest](../Topic/CMFCToolBarButton::OnToolHitTest.md)|Llamado por el marco cuando la barra de herramientas principal debe determinar si un punto está en el rectángulo delimitador del botón.|  
|[CMFCToolBarButton::OnUpdateToolTip](../Topic/CMFCToolBarButton::OnUpdateToolTip.md)|Llamado por el marco cuando la barra de herramientas principal actualiza el texto de información sobre herramientas.|  
|[CMFCToolBarButton::PrepareDrag](../Topic/CMFCToolBarButton::PrepareDrag.md)|Llamado por el marco cuando el botón está a punto de realizar una operación de arrastrar y colocar.|  
|[CMFCToolBarButton::Rect](../Topic/CMFCToolBarButton::Rect.md)|Recupera el rectángulo delimitador del botón.|  
|[CMFCToolBarButton::ResetImageToDefault](../Topic/CMFCToolBarButton::ResetImageToDefault.md)|Establece el valor predeterminado la imagen que está asociado al botón.|  
|[CMFCToolBarButton::SaveBarState](../Topic/CMFCToolBarButton::SaveBarState.md)|Guarda el estado del botón de la barra de herramientas.|  
|[CMFCToolBarButton::Serialize](../Topic/CMFCToolBarButton::Serialize.md)|Lee este objeto de un archivo o de escribe en un archivo.  \(Reemplaza [CObject::Serialize](../Topic/CObject::Serialize.md).\)|  
|[CMFCToolBarButton::SetACCData](../Topic/CMFCToolBarButton::SetACCData.md)|Rellena el objeto proporcionado de `CAccessibilityData` con datos de accesibilidad del botón de la barra de herramientas.|  
|[CMFCToolBarButton::SetClipboardFormatName](../Topic/CMFCToolBarButton::SetClipboardFormatName.md)|Cambiar el formato global del portapapeles.|  
|[CMFCToolBarButton::SetImage](../Topic/CMFCToolBarButton::SetImage.md)|Establece el índice del botón.|  
|[CMFCToolBarButton::SetProtectedCommands](../Topic/CMFCToolBarButton::SetProtectedCommands.md)|establece la lista de comandos que el usuario no puede personalizar.|  
|[CMFCToolBarButton::SetRadio](../Topic/CMFCToolBarButton::SetRadio.md)|Llamado por el marco cuando un botón cambia su estado activada.|  
|[CMFCToolBarButton::SetRect](../Topic/CMFCToolBarButton::SetRect.md)|Establece el rectángulo delimitador del botón.|  
|[CMFCToolBarButton::SetStyle](../Topic/CMFCToolBarButton::SetStyle.md)|Establece el estilo de botón.|  
|[CMFCToolBarButton::SetVisible](../Topic/CMFCToolBarButton::SetVisible.md)|Especifica si el botón está visible.|  
|[CMFCToolBarButton::Show](../Topic/CMFCToolBarButton::Show.md)|Muestra u oculta el botón.|  
  
### miembros de datos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCToolBarButton::m\_bImage](../Topic/CMFCToolBarButton::m_bImage.md)|Especifica si una imagen se muestra en el botón.|  
|[CMFCToolBarButton::m\_bText](../Topic/CMFCToolBarButton::m_bText.md)|Especifica si una etiqueta de texto se muestra en el botón.|  
|[CMFCToolBarButton::m\_bTextBelow](../Topic/CMFCToolBarButton::m_bTextBelow.md)|Especifica si el etiqueta de texto se muestra bajo la imagen en el botón.|  
|[CMFCToolBarButton::m\_bUserButton](../Topic/CMFCToolBarButton::m_bUserButton.md)|Especifica si el botón con una imagen definido por el usuario.|  
|[CMFCToolBarButton::m\_bWholeText](../Topic/CMFCToolBarButton::m_bWholeText.md)|Especifica si el botón muestra la etiqueta de texto completo incluso si no cabe en el rectángulo delimitador.|  
|[CMFCToolBarButton::m\_bWrap](../Topic/CMFCToolBarButton::m_bWrap.md)|Especifica si el botón situado junto a un separador se colocará en la fila siguiente.|  
|[CMFCToolBarButton::m\_bWrapText](../Topic/CMFCToolBarButton::m_bWrapText.md)|Especifica si las etiquetas de texto multilínea están habilitados.|  
|[CMFCToolBarButton::m\_nID](../Topic/CMFCToolBarButton::m_nID.md)|El identificador de comando del botón.|  
|[CMFCToolBarButton::m\_nStyle](../Topic/CMFCToolBarButton::m_nStyle.md)|El estilo de botón.|  
|[CMFCToolBarButton::m\_strText](../Topic/CMFCToolBarButton::m_strText.md)|La etiqueta de texto del botón.|  
  
## Comentarios  
 Un objeto de `CMFCToolbarButton` es un control que residen en una barra de herramientas.  Su comportamiento es similar al de un botón normal.  Puede asignar una imagen y una etiqueta de texto a este objeto.  Un botón de la barra de herramientas también puede tener un identificador de comando  Cuando el usuario hace clic en el botón de la barra de herramientas, el marco ejecuta el comando que este identificador especifica.  
  
 Normalmente, los botones de la barra de herramientas pueden ser personalizados: el usuario puede arrastrar los botones a partir de una barra de herramientas a otra, y copiar, pegar, delete, y las etiquetas de texto y las imágenes de edición.  Para evitar que el usuario personalizar la barra de herramientas, puede bloquear la barra de herramientas de dos maneras.  Cualquiera establece la marca de `bLocked` a `TRUE` cuando se llama a [CMFCToolBar::LoadToolBar](../Topic/CMFCToolBar::LoadToolBar.md), o agrega el identificador de comando de un botón individual de la lista global de comandos protegidos mediante el método de [CMFCToolBarButton::SetProtectedCommands](../Topic/CMFCToolBarButton::SetProtectedCommands.md) .  
  
 imágenes de presentación de los objetos de`CMFCToolBarButton` de las colecciones globales de imágenes de la barra de herramientas en la aplicación.  Estas colecciones son mantenidas por la barra de herramientas principal, [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md).  Para obtener más información, vea [CMFCToolBarImages Class](../../mfc/reference/cmfctoolbarimages-class.md).  
  
 Cuando el usuario hace clic en un botón de la barra de herramientas, la barra de herramientas principal procesa el mensaje del mouse y comunica acciones adecuados al botón.  Si el botón tiene un identificador válido del comando, la barra de herramientas principal envía el mensaje de `WM_COMMAND` el cuadro primario.  
  
 La clase de `CMFCToolBarButton` es la clase base para otras clases de botón de la barra de herramientas, como [CMFCToolBarMenuButton Class](../../mfc/reference/cmfctoolbarmenubutton-class.md), [CMFCToolBarEditBoxButton Class](../../mfc/reference/cmfctoolbareditboxbutton-class.md), y [CMFCToolBarComboBoxButton Class](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md).  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo configurar un objeto de `CMFCToolBarButton` mediante varios métodos en la clase de `CMFCToolBarButton` .  El ejemplo muestra cómo habilitar la entrada del mouse y del teclado, establecer el índice del botón, establecer el rectángulo delimitador del botón, y crear el botón visible.  Este fragmento de código es parte de [ejemplo de Tab Control](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_TabControl#1](../../mfc/reference/codesnippet/CPP/cmfctoolbarbutton-class_1.cpp)]  
[!code-cpp[NVC_MFC_TabControl#2](../../mfc/reference/codesnippet/CPP/cmfctoolbarbutton-class_2.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
## Requisitos  
 **encabezado:** afxtoolbarbutton.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarImages Class](../../mfc/reference/cmfctoolbarimages-class.md)   
 [CMFCToolBarButton::OnClick](../Topic/CMFCToolBarButton::OnClick.md)   
 [CMFCToolBarButton::NotifyCommand](../Topic/CMFCToolBarButton::NotifyCommand.md)