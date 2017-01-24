---
title: "CView Class | Microsoft Docs"
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
  - "CView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ventanas secundarias, vistas"
  - "CView class"
  - "document/view architecture"
  - "frame windows [C++], vistas"
  - "entrada, and view class"
  - "MDI [C++], view windows"
  - "varias vistas"
  - "vista previa de impresión, view windows"
  - "user input [C++], interpreting through view class"
  - "vistas [C++], view classes"
  - "windows [C++], vistas"
ms.assetid: 9cff3c56-7564-416b-b9a4-71a9254ed755
caps.latest.revision: 25
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona la funcionalidad básica para las clases definidas por el usuario de la vista.  
  
## Sintaxis  
  
```  
class AFX_NOVTABLE CView : public CWnd  
```  
  
## Miembros  
  
### Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CView::CView](../Topic/CView::CView.md)|Crea un objeto `CView`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CView::DoPreparePrinting](../Topic/CView::DoPreparePrinting.md)|El cuadro de diálogo imprimir de muestra y crea contexto de dispositivo de impresora; llamada a reemplazar la función miembro de `OnPreparePrinting` .|  
|[CView::GetDocument](../Topic/CView::GetDocument.md)|Devuelve el documento asociado a la vista.|  
|[CView::IsSelected](../Topic/CView::IsSelected.md)|Comprueba si un elemento de documento está seleccionado.  Necesario para la compatibilidad de OLE.|  
|[CView::OnDragEnter](../Topic/CView::OnDragEnter.md)|Se invoca cuando un elemento primero se arrastra en la región de arrastrar y colocar de una vista.|  
|[CView::OnDragLeave](../Topic/CView::OnDragLeave.md)|Llamado cuando un elemento arrastrado sale de la zona de arrastrar y colocar de una vista.|  
|[CView::OnDragOver](../Topic/CView::OnDragOver.md)|Se invoca cuando un elemento se arrastra a la región de arrastrar y colocar de una vista.|  
|[CView::OnDragScroll](../Topic/CView::OnDragScroll.md)|Denominado para determinar si el cursor se arrastra del área de desplazamiento de la ventana.|  
|[CView::OnDrop](../Topic/CView::OnDrop.md)|Se invoca cuando un elemento se ha quitado de la región de arrastrar y colocar de una vista, controlador predeterminado.|  
|[CView::OnDropEx](../Topic/CView::OnDropEx.md)|Se invoca cuando un elemento se ha quitado de la región de arrastrar y colocar de una vista, controlador primario.|  
|[CView::OnInitialUpdate](../Topic/CView::OnInitialUpdate.md)|Se llama después de que una vista primero se asocia a un documento.|  
|[CView::OnPrepareDC](../Topic/CView::OnPrepareDC.md)|Se llama antes de que la función miembro de `OnDraw` se denomina para la presentación en pantalla o la función miembro de `OnPrint` se denomina para imprimir o la vista previa de impresión.|  
|[CView::OnScroll](../Topic/CView::OnScroll.md)|Se invoca cuando los elementos de OLE se arrastran más allá de los bordes de la vista.|  
|[CView::OnScrollBy](../Topic/CView::OnScrollBy.md)|Llamado cuando una vista que contiene elementos de OLE en contexto activo se desplaza.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CView::OnActivateFrame](../Topic/CView::OnActivateFrame.md)|Llamado cuando la ventana de marco que contiene la vista se activa o desactiva.|  
|[CView::OnActivateView](../Topic/CView::OnActivateView.md)|Llamado cuando se genera una vista.|  
|[CView::OnBeginPrinting](../Topic/CView::OnBeginPrinting.md)|Llamado cuando se inicia un trabajo de impresión; reemplace para asignar recursos de la interfaz de \(GDI\) dispositivo gráfico.|  
|[CView::OnDraw](../Topic/CView::OnDraw.md)|Denominado para representar una imagen del documento para la presentación en pantalla, la impresión, o la vista previa de impresión.  Implementación necesaria.|  
|[CView::OnEndPrinting](../Topic/CView::OnEndPrinting.md)|Se llama cuando finaliza de un trabajo de impresión; reemplace para desasignar los recursos de GDI.|  
|[CView::OnEndPrintPreview](../Topic/CView::OnEndPrintPreview.md)|Se invoca cuando proporcionan salida al modo de vista previa.|  
|[CView::OnPreparePrinting](../Topic/CView::OnPreparePrinting.md)|Se llama antes de que se imprima o se genere una vista previa de un documento; reemplace para inicializar cuadro de diálogo imprimir.|  
|[CView::OnPrint](../Topic/CView::OnPrint.md)|Denominado para imprimir u ofrecer una vista previa de una página del documento.|  
|[CView::OnUpdate](../Topic/CView::OnUpdate.md)|Denominado para notificar a una vista que se ha modificado el documento.|  
  
## Comentarios  
 Una vista está asociado a un documento y actúa como intermediario entre el documento y el usuario: la vista representa una imagen del documento en la pantalla o la impresora e interpreta los datos proporcionados por el usuario como operaciones sobre el documento.  
  
 Una vista es un elemento secundario de una ventana de marco.  Más de una vista puede compartir una ventana de marco, como en el caso de una ventana divisora.  La relación entre una clase de vista, una clase de ventana de marco, y una clase de documento establecida por un objeto de `CDocTemplate` .  Cuando el usuario abre una nueva ventana o divide existente, el marco construye una nueva vista y la agrega al documento.  
  
 Una vista se puede asociar a un solo documento, pero un documento puede tener varias vistas asociadas al inmediatamente \(por ejemplo, si el documento se muestra en una ventana divisora o en ventanas secundarias de una aplicación \(MDI\) de interfaz de múltiples documentos.  La aplicación puede admitir distintos tipos de vista para un tipo de documento determinado; por ejemplo, un procesador de textos podría proporcionar una vista de texto completa de un documento y un contorno ver solo muestra los encabezados de la sección.  Estos tipos diferentes de vistas pueden colocar en ventanas independientes de marco o en paneles diferentes de una sola ventana cuadro si utiliza una ventana divisora.  
  
 Una vista puede ser responsable de administrar varios tipos de entrada, como entrada de teclado, la entrada del mouse o entrada mediante arrastrar y colocar, así como los comandos de menús, barras de herramientas, o de las barras de desplazamiento.  Una vista recibe los comandos reenviados por su ventana de marco.  Si la vista no controla un comando determinado, transmite el comando el documento asociado.  Como todos los destinos de comando, vista controla mensajes mediante un mapa de mensajes.  
  
 La vista es responsable de mostrar y modificar los datos de documento pero no de almacenarla.  El documento proporciona la vista con detalles necesarios en los datos.  Puede dejar los miembros de datos acceso de vista de documentos directamente, o puede proporcionar funciones miembro de la clase document para la clase de vista a la llamada.  
  
 Cuando los cambios de los datos de un documento, la vista responsable de los cambios llama normalmente la función de [CDocument:: UpdateAllViews](../Topic/CDocument::UpdateAllViews.md) para el documento, que notifica al resto de vistas llamando a la función miembro de `OnUpdate` para cada uno.  La implementación predeterminada de `OnUpdate` reemplaza el área cliente completa de la vista.  Puede reemplazarlo para reemplazar solamente las regiones del área de cliente que se asignan a las partes modificadas del documento.  
  
 Para utilizar `CView`, derive una clase de ella y implementar la función miembro de `OnDraw` para realizar la presentación en pantalla.  También puede utilizar `OnDraw` para realizar la impresión y vista previa de impresión.  El marco controla el bucle de impresión para imprimir y obtener una vista previa del documento.  
  
 Una vista controla mensajes de la barra de desplazamiento con las funciones miembro de [CWnd:: OnHScroll](../Topic/CWnd::OnHScroll.md) y de [CWnd:: OnVScroll](../Topic/CWnd::OnVScroll.md) .  Puede implementar el control de mensajes de la barra de desplazamiento en estas funciones, o la clase derivada [CScrollView](../../mfc/reference/cscrollview-class.md) de `CView` para controlar el desplazamiento automáticamente.  
  
 Además de `CScrollView`, la biblioteca Microsoft Foundation Class proporciona nueve otras clases derivadas de `CView`:  
  
-   [CCtrlView](../../mfc/reference/cctrlview-class.md), una vista que permite el uso de la arquitectura de la vista del documento con el árbol, la lista, y los controles rich edit.  
  
-   [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md), una vista que muestra los registros de una base de datos en controles de cuadro de diálogo.  
  
-   [CEditView](../../mfc/reference/ceditview-class.md), una vista que proporciona un editor de texto multilínea simple.  Puede utilizar un objeto de `CEditView` como control en un cuadro de diálogo así como una vista de un documento.  
  
-   [CFormView](../../mfc/reference/cformview-class.md), vista desplazable que contiene controles de cuadro de diálogo y se basa en un recurso de plantilla de cuadro de diálogo.  
  
-   [CListView](../../mfc/reference/clistview-class.md), una vista que permite el uso de la arquitectura de la vista del documento con los controles de lista.  
  
-   [CRecordView](../../mfc/reference/crecordview-class.md), una vista que muestra los registros de una base de datos en controles de cuadro de diálogo.  
  
-   [CRichEditView](../../mfc/reference/cricheditview-class.md), una vista que permite el uso de la arquitectura de la vista del documento con controles rich edit.  
  
-   [CScrollView](../../mfc/reference/cscrollview-class.md), una vista que automáticamente proporciona compatibilidad de desplazamiento.  
  
-   [CTreeView](../../mfc/reference/ctreeview-class.md), una vista que permite el uso de la arquitectura de la vista del documento con los controles de árbol.  
  
 La clase de `CView` tiene también una clase derivada de implementación denominada **CPreviewView**, que utiliza el marco para realizar obtener una vista previa de impresión.  Esta clase proporciona compatibilidad para las características únicas de la ventana, como una barra de herramientas, una vista previa única o de la doble\-página, y el zoom, es decir, agrandando la imagen ofrecida una vista previa.  No necesita llamar o reemplazar a cualquier miembro de CPreviewView funciona a menos que desee implementar para formar la interfaz para la vista previa de impresión \(por ejemplo, si desea admitir la edición en modo vista previa de impresión\).  Para obtener más información sobre cómo utilizar `CView`, vea [Arquitectura documento\/vista](../../mfc/document-view-architecture.md) y [el imprimir](../../mfc/printing.md).  Además, vea [nota técnica 30](../../mfc/tn030-customizing-printing-and-print-preview.md) para más detalles en personalizar la vista previa de impresión.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CView`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [ejemplo MDIDOCVW de MFC](../../top/visual-cpp-samples.md)   
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [CFrameWnd Class](../../mfc/reference/cframewnd-class.md)   
 [CSplitterWnd Class](../../mfc/reference/csplitterwnd-class.md)   
 [CDC \(clase\)](../../mfc/reference/cdc-class.md)   
 [CDocTemplate Class](../../mfc/reference/cdoctemplate-class.md)   
 [CDocument Class](../../mfc/reference/cdocument-class.md)