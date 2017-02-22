---
title: "CRichEditView Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CRichEditView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRichEditView class"
  - "document/view architecture, controles Rich Edit"
  - "OLE containers, rich edit"
  - "controles Rich Edit, OLE container"
ms.assetid: bd576b10-4cc0-4050-8f76-e1a0548411e4
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CRichEditView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Con [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) y [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md), proporciona la funcionalidad del control rich edit en el contexto de la arquitectura de la vista del documento de MFC.  
  
## Sintaxis  
  
```  
  
class CRichEditView : public CCtrlView  
  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRichEditView::CRichEditView](../Topic/CRichEditView::CRichEditView.md)|Crea un objeto `CRichEditView`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRichEditView::AdjustDialogPosition](../Topic/CRichEditView::AdjustDialogPosition.md)|Mueve un cuadro de diálogo para que no oculte la selección actual.|  
|[CRichEditView::CanPaste](../Topic/CRichEditView::CanPaste.md)|Indica si el portapapeles contiene los datos que se pueden pegar en la vista completa de la edición.|  
|[CRichEditView::DoPaste](../Topic/CRichEditView::DoPaste.md)|Pega un elemento OLE en esta vista completa de la edición.|  
|[CRichEditView::FindText](../Topic/CRichEditView::FindText.md)|Encuentra el texto especificado, invocando el cursor de espera.|  
|[CRichEditView::FindTextSimple](../Topic/CRichEditView::FindTextSimple.md)|encuentra el texto especificado.|  
|[CRichEditView::GetCharFormatSelection](../Topic/CRichEditView::GetCharFormatSelection.md)|Recupera los atributos de formato de caracteres para la selección actual.|  
|[CRichEditView::GetDocument](../Topic/CRichEditView::GetDocument.md)|recupera un puntero a [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)relacionado.|  
|[CRichEditView::GetInPlaceActiveItem](../Topic/CRichEditView::GetInPlaceActiveItem.md)|Recupera el elemento OLE que está actualmente activo en contexto en la vista completa de la edición.|  
|[CRichEditView::GetMargins](../Topic/CRichEditView::GetMargins.md)|Recupera los márgenes de esta vista completa de la edición.|  
|[CRichEditView::GetPageRect](../Topic/CRichEditView::GetPageRect.md)|Recupera el rectángulo para esta vista completa de la edición.|  
|[CRichEditView::GetPaperSize](../Topic/CRichEditView::GetPaperSize.md)|Recupera el tamaño del papel para esta vista completa de la edición.|  
|[CRichEditView::GetParaFormatSelection](../Topic/CRichEditView::GetParaFormatSelection.md)|Recupera los atributos de formato de párrafo para la selección actual.|  
|[CRichEditView::GetPrintRect](../Topic/CRichEditView::GetPrintRect.md)|Recupera el rectángulo de impresión para esta vista completa de la edición.|  
|[CRichEditView::GetPrintWidth](../Topic/CRichEditView::GetPrintWidth.md)|Recupera el ancho de impresión para esta vista completa de la edición.|  
|[CRichEditView::GetRichEditCtrl](../Topic/CRichEditView::GetRichEditCtrl.md)|Recupera el control rich edit.|  
|[CRichEditView::GetSelectedItem](../Topic/CRichEditView::GetSelectedItem.md)|Recupera el elemento seleccionado de la vista completa de la edición.|  
|[CRichEditView::GetTextLength](../Topic/CRichEditView::GetTextLength.md)|Recupera la longitud del texto en la vista completa de la edición.|  
|[CRichEditView::GetTextLengthEx](../Topic/CRichEditView::GetTextLengthEx.md)|Recupera el número de caracteres o bytes en la vista completa de la edición.  Marcador expandido enumerado para el método de determinar la longitud.|  
|[CRichEditView::InsertFileAsObject](../Topic/CRichEditView::InsertFileAsObject.md)|Inserta un archivo como elemento.|  
|[CRichEditView::InsertItem](../Topic/CRichEditView::InsertItem.md)|Inserta un nuevo elemento como elemento.|  
|[CRichEditView::IsRichEditFormat](../Topic/CRichEditView::IsRichEditFormat.md)|Indica si el portapapeles contiene datos en una edición o formato de texto completa.|  
|[CRichEditView::OnCharEffect](../Topic/CRichEditView::OnCharEffect.md)|alterna el formato de caracteres para la selección actual.|  
|[CRichEditView::OnParaAlign](../Topic/CRichEditView::OnParaAlign.md)|Cambia la alineación de los párrafos.|  
|[CRichEditView::OnUpdateCharEffect](../Topic/CRichEditView::OnUpdateCharEffect.md)|Actualiza la interfaz de usuario de comandos en las funciones públicas del miembro del carácter.|  
|[CRichEditView::OnUpdateParaAlign](../Topic/CRichEditView::OnUpdateParaAlign.md)|Actualiza la interfaz de usuario de comandos en las funciones públicas del miembro del párrafo.|  
|[CRichEditView::PrintInsideRect](../Topic/CRichEditView::PrintInsideRect.md)|Da formato al texto especificado dentro del rectángulo especificado.|  
|[CRichEditView::PrintPage](../Topic/CRichEditView::PrintPage.md)|Da formato al texto especificado dentro de la página determinada.|  
|[CRichEditView::SetCharFormat](../Topic/CRichEditView::SetCharFormat.md)|Establece los atributos de formato de caracteres para la selección actual.|  
|[CRichEditView::SetMargins](../Topic/CRichEditView::SetMargins.md)|Establece los márgenes de esta vista completa de la edición.|  
|[CRichEditView::SetPaperSize](../Topic/CRichEditView::SetPaperSize.md)|Establece el tamaño del papel para esta vista completa de la edición.|  
|[CRichEditView::SetParaFormat](../Topic/CRichEditView::SetParaFormat.md)|Establece los atributos de formato de párrafo para la selección actual.|  
|[CRichEditView::TextNotFound](../Topic/CRichEditView::TextNotFound.md)|Restablece el estado interno de búsqueda del control.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRichEditView::GetClipboardData](../Topic/CRichEditView::GetClipboardData.md)|Recupera un objeto del portapapeles para un intervalo en esta vista completa de la edición.|  
|[CRichEditView::GetContextMenu](../Topic/CRichEditView::GetContextMenu.md)|Recupera un menú contextual para utilizar en un botón secundario del mouse.|  
|[CRichEditView::IsSelected](../Topic/CRichEditView::IsSelected.md)|Indica si el elemento OLE especificado es seleccionada o no.|  
|[CRichEditView::OnFindNext](../Topic/CRichEditView::OnFindNext.md)|Encuentra la siguiente aparición de una subcadena.|  
|[CRichEditView::OnInitialUpdate](../Topic/CRichEditView::OnInitialUpdate.md)|Actualiza una vista cuando primero está asociado a un documento.|  
|[CRichEditView::OnPasteNativeObject](../Topic/CRichEditView::OnPasteNativeObject.md)|Recupera datos nativos de un elemento.|  
|[CRichEditView::OnPrinterChanged](../Topic/CRichEditView::OnPrinterChanged.md)|Establece las características de impresión al dispositivo especificado.|  
|[CRichEditView::OnReplaceAll](../Topic/CRichEditView::OnReplaceAll.md)|Reemplaza todas las apariciones de una cadena especificada por una cadena nueva.|  
|[CRichEditView::OnReplaceSel](../Topic/CRichEditView::OnReplaceSel.md)|reemplaza la selección actual.|  
|[CRichEditView::OnTextNotFound](../Topic/CRichEditView::OnTextNotFound.md)|Controla la notificación de usuario que el texto solicitado no encontrado.|  
|[CRichEditView::QueryAcceptData](../Topic/CRichEditView::QueryAcceptData.md)|Consultas consultar los datos de `IDataObject`.|  
|[CRichEditView::WrapChanged](../Topic/CRichEditView::WrapChanged.md)|Ajusta el dispositivo de salida de destino para esta vista completa de edición, según el valor de `m_nWordWrap`.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRichEditView::m\_nBulletIndent](../Topic/CRichEditView::m_nBulletIndent.md)|Indica la cantidad de sangría para listas de viñetas.|  
|[CRichEditView::m\_nWordWrap](../Topic/CRichEditView::m_nWordWrap.md)|Indica las restricciones de ajuste de línea.|  
  
## Comentarios  
 Un “control rich edit” es una ventana en la que el usuario puede escribir y modificar texto.  el texto se puede asignar el carácter y el formato de párrafo, y puede incluir objetos OLE incrustados.  Los controles rich edit proporcionan una interfaz de programación para dar formato al texto.  Sin embargo, una aplicación debe implementar cualquier componente de la interfaz de usuario necesario colocar operaciones de formato a disposición del usuario.  
  
 `CRichEditView` mantiene el texto y la característica de formato de texto.  `CRichEditDoc` mantiene la lista de elementos de OLE de cliente que están en la vista.  `CRichEditCntrItem` proporciona acceso de contenedor\-lado el elemento OLE de cliente.  
  
 Este control común de Windows \(y por consiguiente [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) y las clases relacionadas\) sólo está disponible para los programas que se ejecutan en versiones de Windows 3,51 95 \/98 y Windows NT y posterior.  
  
 Para obtener un ejemplo de cómo utilizar una vista completa de edición en una aplicación MFC, vea la aplicación de ejemplo de [WORDPAD](../../top/visual-cpp-samples.md) .  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CCtrlView](../../mfc/reference/cctrlview-class.md)  
  
 `CRichEditView`  
  
## Requisitos  
 **encabezado:** afxrich.h  
  
## Vea también  
 [ejemplo WORDPAD de MFC](../../top/visual-cpp-samples.md)   
 [CCtrlView Class](../../mfc/reference/cctrlview-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CRichEditDoc Class](../../mfc/reference/cricheditdoc-class.md)   
 [CRichEditCntrItem Class](../../mfc/reference/cricheditcntritem-class.md)