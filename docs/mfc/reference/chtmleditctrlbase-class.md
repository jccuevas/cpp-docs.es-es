---
title: "CHtmlEditCtrlBase Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CHtmlEditCtrlBase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHtmlEditCtrlBase class"
ms.assetid: e0cc74b4-8320-4570-b673-16c03d2ae266
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CHtmlEditCtrlBase Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa un componente de edición HTML.  
  
## Sintaxis  
  
```  
  
template < class   
T  
 > class CHtmlEditCtrlBase  
  
```  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHtmlEditCtrlBase::AddToGlyphTable](../Topic/CHtmlEditCtrlBase::AddToGlyphTable.md)|Agrega una entrada a la tabla de glifo, que especifica imágenes para mostrar para las etiquetas específicas en modo de diseño.|  
|[CHtmlEditCtrlBase::Bold](../Topic/CHtmlEditCtrlBase::Bold.md)|Alterna el estado de negrita del texto seleccionado.|  
|[CHtmlEditCtrlBase::Button](../Topic/CHtmlEditCtrlBase::Button.md)|Sobrescribe un control button a la selección actual.|  
|[CHtmlEditCtrlBase::CheckBox](../Topic/CHtmlEditCtrlBase::CheckBox.md)|Sobrescribe un control checkbox a la selección actual.|  
|[CHtmlEditCtrlBase::ClearSelection](../Topic/CHtmlEditCtrlBase::ClearSelection.md)|Borra la selección actual.|  
|[CHtmlEditCtrlBase::Copy](../Topic/CHtmlEditCtrlBase::Copy.md)|Copia la selección actual en el portapapeles.|  
|[CHtmlEditCtrlBase::Cut](../Topic/CHtmlEditCtrlBase::Cut.md)|Copia la selección actual en el portapapeles y la elimina.|  
|[CHtmlEditCtrlBase::Delete](../Topic/CHtmlEditCtrlBase::Delete.md)|elimina la selección actual.|  
|[CHtmlEditCtrlBase::DropDownBox](../Topic/CHtmlEditCtrlBase::DropDownBox.md)|sobrescribe un control de selección desplegable en la selección actual.|  
|[CHtmlEditCtrlBase::EmptyGlyphTable](../Topic/CHtmlEditCtrlBase::EmptyGlyphTable.md)|Quita todas las entradas de la tabla del glifo, que oculta todas las imágenes mostradas para las etiquetas en modo de diseño.|  
|[CHtmlEditCtrlBase::ExecCommand](../Topic/CHtmlEditCtrlBase::ExecCommand.md)|ejecuta un comando.|  
|[CHtmlEditCtrlBase::Font](../Topic/CHtmlEditCtrlBase::Font.md)|Abre un cuadro de diálogo fuente para permitir al usuario cambiar el color del texto, la fuente, y el tamaño de fuente de la selección actual.|  
|[CHtmlEditCtrlBase::GetAbsolutePosition](../Topic/CHtmlEditCtrlBase::GetAbsolutePosition.md)|Devuelve si la propiedad position de un elemento es “absolute”.|  
|[CHtmlEditCtrlBase::GetBackColor](../Topic/CHtmlEditCtrlBase::GetBackColor.md)|recupera el color de fondo de la selección actual.|  
|[CHtmlEditCtrlBase::GetBlockFormat](../Topic/CHtmlEditCtrlBase::GetBlockFormat.md)|Recupera la etiqueta actual de formato de bloque.|  
|[CHtmlEditCtrlBase::GetBlockFormatNames](../Topic/CHtmlEditCtrlBase::GetBlockFormatNames.md)|Recupera las cadenas correspondiente a las etiquetas disponibles de formato de bloque.|  
|[CHtmlEditCtrlBase::GetBookMark](../Topic/CHtmlEditCtrlBase::GetBookMark.md)|Recupera el nombre de un delimitador de marcador.|  
|[CHtmlEditCtrlBase::GetDocument](../Topic/CHtmlEditCtrlBase::GetDocument.md)|Recupera el objeto de documento.|  
|[CHtmlEditCtrlBase::GetDocumentHTML](../Topic/CHtmlEditCtrlBase::GetDocumentHTML.md)|Recupera HTML del documento actual.|  
|[CHtmlEditCtrlBase::GetDocumentTitle](../Topic/CHtmlEditCtrlBase::GetDocumentTitle.md)|Recupera el título del documento.|  
|[CHtmlEditCtrlBase::GetEvent](../Topic/CHtmlEditCtrlBase::GetEvent.md)|Recupera un puntero de interfaz al objeto de evento que contiene información relevante para el evento más reciente.|  
|[CHtmlEditCtrlBase::GetEventSrcElement](../Topic/CHtmlEditCtrlBase::GetEventSrcElement.md)|recupera el objeto que desencadenó el evento.|  
|[CHtmlEditCtrlBase::GetFontFace](../Topic/CHtmlEditCtrlBase::GetFontFace.md)|recupera el nombre de fuente para la selección actual.|  
|[CHtmlEditCtrlBase::GetFontSize](../Topic/CHtmlEditCtrlBase::GetFontSize.md)|Recupera el tamaño de fuente de la selección actual.|  
|[CHtmlEditCtrlBase::GetForeColor](../Topic/CHtmlEditCtrlBase::GetForeColor.md)|Recupera el primer plano \(texto\) el color de la selección actual.|  
|[CHtmlEditCtrlBase::GetFrameZone](../Topic/CHtmlEditCtrlBase::GetFrameZone.md)|Devuelve la zona de seguridad de la página actual en el explorador web.|  
|[CHtmlEditCtrlBase::GetIsDirty](../Topic/CHtmlEditCtrlBase::GetIsDirty.md)|indica si el documento HTML ha cambiado.|  
|[CHtmlEditCtrlBase::GetShowAlignedSiteTags](../Topic/CHtmlEditCtrlBase::GetShowAlignedSiteTags.md)|Devuelve si un glifo aparece para todos los elementos que tengan una propiedad de **styleFloat** .|  
|[CHtmlEditCtrlBase::GetShowAllTags](../Topic/CHtmlEditCtrlBase::GetShowAllTags.md)|Devuelve si el WebBrowser muestran glifos para mostrar la ubicación de todas las etiquetas de un documento.|  
|[CHtmlEditCtrlBase::GetShowAreaTags](../Topic/CHtmlEditCtrlBase::GetShowAreaTags.md)|Recupera si el WebBrowser muestra un glifo de las etiquetas de área.|  
|[CHtmlEditCtrlBase::GetShowBRTags](../Topic/CHtmlEditCtrlBase::GetShowBRTags.md)|Recupera si el WebBrowser muestra un glifo de las etiquetas de Br.|  
|[CHtmlEditCtrlBase::GetShowCommentTags](../Topic/CHtmlEditCtrlBase::GetShowCommentTags.md)|Recupera si el WebBrowser muestra un glifo de las etiquetas de comentario.|  
|[CHtmlEditCtrlBase::GetShowMiscTags](../Topic/CHtmlEditCtrlBase::GetShowMiscTags.md)|Recupera si el WebBrowser muestra todas las etiquetas mostradas en Microsoft Internet Explorer 4,0.|  
|[CHtmlEditCtrlBase::GetShowScriptTags](../Topic/CHtmlEditCtrlBase::GetShowScriptTags.md)|Recupera si el WebBrowser muestra un glifo para todas las etiquetas script.|  
|[CHtmlEditCtrlBase::GetShowStyleTags](../Topic/CHtmlEditCtrlBase::GetShowStyleTags.md)|Recupera si el WebBrowser muestra un glifo de todas las etiquetas de estilo.|  
|[CHtmlEditCtrlBase::GetShowUnknownTags](../Topic/CHtmlEditCtrlBase::GetShowUnknownTags.md)|Recupera si el WebBrowser muestra un glifo de todas las etiquetas desconocidas.|  
|[CHtmlEditCtrlBase::HorizontalLine](../Topic/CHtmlEditCtrlBase::HorizontalLine.md)|sobrescribe una línea horizontal en la selección actual.|  
|[CHtmlEditCtrlBase::HyperLink](../Topic/CHtmlEditCtrlBase::HyperLink.md)|inserta un hipervínculo en la selección actual.|  
|[CHtmlEditCtrlBase::IE50Paste](../Topic/CHtmlEditCtrlBase::IE50Paste.md)|Realiza un compatible de la operación de pegar con Microsoft Internet Explorer 5.|  
|[CHtmlEditCtrlBase::Iframe](../Topic/CHtmlEditCtrlBase::Iframe.md)|sobrescribe un marco flotante en la selección actual.|  
|[CHtmlEditCtrlBase::Image](../Topic/CHtmlEditCtrlBase::Image.md)|sobrescribe una imagen en la selección actual.|  
|[CHtmlEditCtrlBase::Indent](../Topic/CHtmlEditCtrlBase::Indent.md)|Aumenta la sangría del texto seleccionado en un incremento de sangría.|  
|[CHtmlEditCtrlBase::InsFieldSet](../Topic/CHtmlEditCtrlBase::InsFieldSet.md)|sobrescribe un cuadro en la selección actual.|  
|[CHtmlEditCtrlBase::InsInputButton](../Topic/CHtmlEditCtrlBase::InsInputButton.md)|Sobrescribe un control button a la selección actual.|  
|[CHtmlEditCtrlBase::InsInputHidden](../Topic/CHtmlEditCtrlBase::InsInputHidden.md)|Inserte un control oculto en la selección actual.|  
|[CHtmlEditCtrlBase::InsInputImage](../Topic/CHtmlEditCtrlBase::InsInputImage.md)|Sobrescribe un control image en la selección actual.|  
|[CHtmlEditCtrlBase::InsInputPassword](../Topic/CHtmlEditCtrlBase::InsInputPassword.md)|sobrescribe un control de contraseñas en la selección actual.|  
|[CHtmlEditCtrlBase::InsInputReset](../Topic/CHtmlEditCtrlBase::InsInputReset.md)|Sobrescribe un control de reinicio de la selección actual.|  
|[CHtmlEditCtrlBase::InsInputSubmit](../Topic/CHtmlEditCtrlBase::InsInputSubmit.md)|Sobrescribe un control submit en la selección actual.|  
|[CHtmlEditCtrlBase::InsInputUpload](../Topic/CHtmlEditCtrlBase::InsInputUpload.md)|sobrescribe un control de carga de archivos en la selección actual.|  
|[CHtmlEditCtrlBase::Is1DElement](../Topic/CHtmlEditCtrlBase::Is1DElement.md)|determina si un elemento se coloca estáticamente.|  
|[CHtmlEditCtrlBase::Is2DElement](../Topic/CHtmlEditCtrlBase::Is2DElement.md)|Determina si un elemento se coloca absolutas.|  
|[CHtmlEditCtrlBase::Italic](../Topic/CHtmlEditCtrlBase::Italic.md)|alterna la selección actual entre cursiva y nonitalic.|  
|[CHtmlEditCtrlBase::JustifyCenter](../Topic/CHtmlEditCtrlBase::JustifyCenter.md)|Centra la página formato donde la selección actual se encuentra.|  
|[CHtmlEditCtrlBase::JustifyLeft](../Topic/CHtmlEditCtrlBase::JustifyLeft.md)|alinea la página formato donde la selección actual se encuentra.|  
|[CHtmlEditCtrlBase::JustifyRight](../Topic/CHtmlEditCtrlBase::JustifyRight.md)|Justifica a la derecha la página formato donde la selección actual se encuentra.|  
|[CHtmlEditCtrlBase::ListBox](../Topic/CHtmlEditCtrlBase::ListBox.md)|Sobrescribe un control de selección del cuadro de lista de la selección actual.|  
|[CHtmlEditCtrlBase::Marquee](../Topic/CHtmlEditCtrlBase::Marquee.md)|Sobrescribe una marquesina vacía en la selección actual.|  
|[CHtmlEditCtrlBase::NewDocument](../Topic/CHtmlEditCtrlBase::NewDocument.md)|crea un nuevo documento.|  
|[CHtmlEditCtrlBase::OrderList](../Topic/CHtmlEditCtrlBase::OrderList.md)|Alterna la selección actual entre una lista ordenada y una página formato normal.|  
|[CHtmlEditCtrlBase::Outdent](../Topic/CHtmlEditCtrlBase::Outdent.md)|Reduce en un incremento la sangría de la página formato donde la selección actual se encuentra.|  
|[CHtmlEditCtrlBase::Paragraph](../Topic/CHtmlEditCtrlBase::Paragraph.md)|Sobrescribe un salto de línea de la selección actual.|  
|[CHtmlEditCtrlBase::Paste](../Topic/CHtmlEditCtrlBase::Paste.md)|Sobrescribe el contenido del portapapeles en la selección actual.|  
|[CHtmlEditCtrlBase::PrintDocument](../Topic/CHtmlEditCtrlBase::PrintDocument.md)|imprime el documento actual.|  
|[CHtmlEditCtrlBase::PrintPreview](../Topic/CHtmlEditCtrlBase::PrintPreview.md)|Abra la ventana de vista previa del documento actual mediante la plantilla predeterminada de vista previa de impresión o una plantilla personalizada.|  
|[CHtmlEditCtrlBase::QueryStatus](../Topic/CHtmlEditCtrlBase::QueryStatus.md)|Llame a este método para ver el estado de comandos.|  
|[CHtmlEditCtrlBase::RadioButton](../Topic/CHtmlEditCtrlBase::RadioButton.md)|sobrescribe un control de radio en la selección actual.|  
|[CHtmlEditCtrlBase::RefreshDocument](../Topic/CHtmlEditCtrlBase::RefreshDocument.md)|actualiza el documento actual.|  
|[CHtmlEditCtrlBase::RemoveFormat](../Topic/CHtmlEditCtrlBase::RemoveFormat.md)|Quita las etiquetas de formato de la selección actual.|  
|[CHtmlEditCtrlBase::SaveAs](../Topic/CHtmlEditCtrlBase::SaveAs.md)|Guarda la página Web actual en un archivo.|  
|[CHtmlEditCtrlBase::SelectAll](../Topic/CHtmlEditCtrlBase::SelectAll.md)|Selecciona todo el documento.|  
|[CHtmlEditCtrlBase::Set2DPosition](../Topic/CHtmlEditCtrlBase::Set2DPosition.md)|Permite que los elementos con posición absoluta son desplazados arrastrando.|  
|[CHtmlEditCtrlBase::SetAbsolutePosition](../Topic/CHtmlEditCtrlBase::SetAbsolutePosition.md)|Establece la propiedad “absolute” o “static de la posición de un elemento”.|  
|[CHtmlEditCtrlBase::SetAtomicSelection](../Topic/CHtmlEditCtrlBase::SetAtomicSelection.md)|modo atómico determinado de la selección.|  
|[CHtmlEditCtrlBase::SetAutoURLDetectMode](../Topic/CHtmlEditCtrlBase::SetAutoURLDetectMode.md)|Activa la detección automática de la dirección URL por intervalos.|  
|[CHtmlEditCtrlBase::SetBackColor](../Topic/CHtmlEditCtrlBase::SetBackColor.md)|establece el color de fondo de la selección actual.|  
|[CHtmlEditCtrlBase::SetBlockFormat](../Topic/CHtmlEditCtrlBase::SetBlockFormat.md)|Establezca la etiqueta actual de formato de bloque.|  
|[CHtmlEditCtrlBase::SetBookMark](../Topic/CHtmlEditCtrlBase::SetBookMark.md)|Crea un marcador delimitar para el punto de selección actual o de inserción.|  
|[CHtmlEditCtrlBase::SetCSSEditingLevel](../Topic/CHtmlEditCtrlBase::SetCSSEditingLevel.md)|Seleccionado CSS nivela \(CSS1 o CSS2\) el editor admitirá, si procede.|  
|[CHtmlEditCtrlBase::SetDefaultComposeSettings](../Topic/CHtmlEditCtrlBase::SetDefaultComposeSettings.md)|Llame a este método para establecer el valor predeterminado constituyen valores.|  
|[CHtmlEditCtrlBase::SetDesignMode](../Topic/CHtmlEditCtrlBase::SetDesignMode.md)|Establezca el modo de diseño.|  
|[CHtmlEditCtrlBase::SetDisableEditFocusUI](../Topic/CHtmlEditCtrlBase::SetDisableEditFocusUI.md)|Deshabilita el borde y los identificadores tramados alrededor de un elemento que tiene el foco de edición.|  
|[CHtmlEditCtrlBase::SetDocumentHTML](../Topic/CHtmlEditCtrlBase::SetDocumentHTML.md)|Establece HTML del documento actual.|  
|[CHtmlEditCtrlBase::SetFontFace](../Topic/CHtmlEditCtrlBase::SetFontFace.md)|Establece la fuente de la selección actual.|  
|[CHtmlEditCtrlBase::SetFontSize](../Topic/CHtmlEditCtrlBase::SetFontSize.md)|Establece el tamaño de fuente de la selección actual.|  
|[CHtmlEditCtrlBase::SetForeColor](../Topic/CHtmlEditCtrlBase::SetForeColor.md)|Establece el primer plano \(texto\) el color de la selección actual.|  
|[CHtmlEditCtrlBase::SetIE5PasteMode](../Topic/CHtmlEditCtrlBase::SetIE5PasteMode.md)|Establece la operación de pegar para ser compatible con Microsoft Internet Explorer 5.|  
|[CHtmlEditCtrlBase::SetLiveResize](../Topic/CHtmlEditCtrlBase::SetLiveResize.md)|Haga el WebBrowser para actualizar el aspecto de un elemento continuamente durante el tamaño o una operación móvil.|  
|[CHtmlEditCtrlBase::SetMultiSelect](../Topic/CHtmlEditCtrlBase::SetMultiSelect.md)|habilita la selección múltiple.|  
|[CHtmlEditCtrlBase::SetOverrideCursor](../Topic/CHtmlEditCtrlBase::SetOverrideCursor.md)|Comandos el WebBrowser nunca de cambiar el puntero del mouse.|  
|[CHtmlEditCtrlBase::SetOverwriteMode](../Topic/CHtmlEditCtrlBase::SetOverwriteMode.md)|Alterna el modo de entrada de texto entre inserción y lo sobrescribe.|  
|[CHtmlEditCtrlBase::SetRespectVisInDesign](../Topic/CHtmlEditCtrlBase::SetRespectVisInDesign.md)|Oculta elementos invisibles en modo de diseño.|  
|[CHtmlEditCtrlBase::SetShowAlignedSiteTags](../Topic/CHtmlEditCtrlBase::SetShowAlignedSiteTags.md)|Muestra un glifo para todos los elementos que tengan una propiedad de **styleFloat** .|  
|[CHtmlEditCtrlBase::SetShowAllTags](../Topic/CHtmlEditCtrlBase::SetShowAllTags.md)|Muestra glifos para mostrar la ubicación de todas las etiquetas de un documento.|  
|[CHtmlEditCtrlBase::SetShowAreaTags](../Topic/CHtmlEditCtrlBase::SetShowAreaTags.md)|Muestra un glifo de todas las etiquetas de área.|  
|[CHtmlEditCtrlBase::SetShowBRTags](../Topic/CHtmlEditCtrlBase::SetShowBRTags.md)|Muestra un glifo de todas las etiquetas de Br.|  
|[CHtmlEditCtrlBase::SetShowCommentTags](../Topic/CHtmlEditCtrlBase::SetShowCommentTags.md)|Muestra un glifo de todas las etiquetas del comentario.|  
|[CHtmlEditCtrlBase::SetShowMiscTags](../Topic/CHtmlEditCtrlBase::SetShowMiscTags.md)|Muestra todas las etiquetas mostradas en Microsoft Internet Explorer 4,0.|  
|[CHtmlEditCtrlBase::SetShowScriptTags](../Topic/CHtmlEditCtrlBase::SetShowScriptTags.md)|Muestra un glifo para todas las etiquetas script.|  
|[CHtmlEditCtrlBase::SetShowStyleTags](../Topic/CHtmlEditCtrlBase::SetShowStyleTags.md)|Muestra un glifo de todas las etiquetas de estilo.|  
|[CHtmlEditCtrlBase::SetShowUnknownTags](../Topic/CHtmlEditCtrlBase::SetShowUnknownTags.md)|Muestra un glifo de todas las etiquetas desconocidas.|  
|[CHtmlEditCtrlBase::TextArea](../Topic/CHtmlEditCtrlBase::TextArea.md)|Sobrescribe un control de entrada de varias líneas de texto en la selección actual.|  
|[CHtmlEditCtrlBase::TextBox](../Topic/CHtmlEditCtrlBase::TextBox.md)|Sobrescribe un control de texto en la selección actual.|  
|[CHtmlEditCtrlBase::UnBookmark](../Topic/CHtmlEditCtrlBase::UnBookmark.md)|quita cualquier marcador de la selección actual.|  
|[CHtmlEditCtrlBase::Underline](../Topic/CHtmlEditCtrlBase::Underline.md)|alterna la selección actual entre subrayado y no subrayado.|  
|[CHtmlEditCtrlBase::Unlink](../Topic/CHtmlEditCtrlBase::Unlink.md)|quita cualquier hipervínculo de la selección actual.|  
|[CHtmlEditCtrlBase::UnorderList](../Topic/CHtmlEditCtrlBase::UnorderList.md)|Alterna la selección actual entre una lista ordenada y una página formato normal.|  
  
#### Parámetros  
 `T`  
 El nombre de la clase derivada.  
  
## Comentarios  
 **CHtmlEditCtrlBase** proporciona funciones miembro para los comandos de edición de HTML de WebBrowser, como [Bold](../Topic/CHtmlEditCtrlBase::Bold.md).  \(Como alternativa, puede llamar a [ExecCommand](../Topic/CHtmlEditCtrlBase::ExecCommand.md) para ejecutar el comando de **IDM\_BOLD** .\)  
  
 **CHtmlEditCtrlBase** no está diseñada para colocarse en solitario.  Está diseñado para ser una clase base para las clases derivadas que exponen la funcionalidad de edición de HTML de WebBrowser \(vea [CHtmlEditCtrl](../../mfc/reference/chtmleditctrl-class.md) y [CHtmlEditView](../../mfc/reference/chtmleditview-class.md)\).  
  
## Jerarquía de herencia  
 `CHtmlEditCtrlBase`  
  
## Requisitos  
 **encabezado:** afxhtml.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Ejemplo HTMLEdit](../../top/visual-cpp-samples.md)