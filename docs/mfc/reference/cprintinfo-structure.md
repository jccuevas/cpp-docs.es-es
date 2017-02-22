---
title: "CPrintInfo Structure | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CPrintInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPrintInfo structure"
ms.assetid: 0b3de849-d050-4386-9a14-f4c1a25684f7
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CPrintInfo Structure
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Información de los almacenes sobre un trabajo de impresión o de la vista previa de impresión.  
  
## Sintaxis  
  
```  
struct CPrintInfo  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPrintInfo::GetFromPage](../Topic/CPrintInfo::GetFromPage.md)|Devuelve el número de la primera página que es impresa.|  
|[CPrintInfo::GetMaxPage](../Topic/CPrintInfo::GetMaxPage.md)|Devuelve el número de la última página del documento.|  
|[CPrintInfo::GetMinPage](../Topic/CPrintInfo::GetMinPage.md)|Devuelve el número de la primera página del documento.|  
|[CPrintInfo::GetOffsetPage](../Topic/CPrintInfo::GetOffsetPage.md)|Devuelve el número de páginas que preceden a la primera página de un elemento de DocObject que se imprimirá en un trabajo de impresión combinado de DocObject.|  
|[CPrintInfo::GetToPage](../Topic/CPrintInfo::GetToPage.md)|Devuelve el número de la última página que se imprimirá.|  
|[CPrintInfo::SetMaxPage](../Topic/CPrintInfo::SetMaxPage.md)|Establece el número de la última página del documento.|  
|[CPrintInfo::SetMinPage](../Topic/CPrintInfo::SetMinPage.md)|Establece el número de la primera página del documento.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPrintInfo::m\_bContinuePrinting](../Topic/CPrintInfo::m_bContinuePrinting.md)|Contiene una marca que indica si el marco debe continuar el bucle de impresión.|  
|[CPrintInfo::m\_bDirect](../Topic/CPrintInfo::m_bDirect.md)|Contiene una marca que indica si el documento se imprime directamente \(sin mostrar el cuadro de diálogo imprimir\).|  
|[CPrintInfo::m\_bDocObject](../Topic/CPrintInfo::m_bDocObject.md)|Contiene una marca que indica si el documento que se va a imprimir es un DocObject.|  
|[CPrintInfo::m\_bPreview](../Topic/CPrintInfo::m_bPreview.md)|Contiene una marca que indica si se encuentra en la vista previa del documento.|  
|[CPrintInfo::m\_dwFlags](../Topic/CPrintInfo::m_dwFlags.md)|Especifica las operaciones de impresión de DocObject.|  
|[CPrintInfo::m\_lpUserData](../Topic/CPrintInfo::m_lpUserData.md)|Contiene un puntero a una estructura creada por el usuario.|  
|[CPrintInfo::m\_nCurPage](../Topic/CPrintInfo::m_nCurPage.md)|Identifica el número de la página que está impresa actualmente.|  
|[CPrintInfo::m\_nJobNumber](../Topic/CPrintInfo::m_nJobNumber.md)|Especifica el número de trabajo asignado por el sistema operativo para el trabajo de impresión actual|  
|[CPrintInfo::m\_nNumPreviewPages](../Topic/CPrintInfo::m_nNumPreviewPages.md)|Identifica el número de páginas que la ventana de vista previa; 1 o 2.|  
|[CPrintInfo::m\_nOffsetPage](../Topic/CPrintInfo::m_nOffsetPage.md)|Especifica el desplazamiento de detalle un DocObject primero paginan en un trabajo de impresión combinado de DocObject.|  
|[CPrintInfo::m\_pPD](../Topic/CPrintInfo::m_pPD.md)|Contiene un puntero al objeto de `CPrintDialog` utilizado para el cuadro de diálogo imprimir.|  
|[CPrintInfo::m\_rectDraw](../Topic/CPrintInfo::m_rectDraw.md)|Especifica un rectángulo que define el área utilizable actual.|  
|[CPrintInfo::m\_strPageDesc](../Topic/CPrintInfo::m_strPageDesc.md)|Contiene una cadena de formato para la presentación de número de página.|  
  
## Comentarios  
 `CPrintInfo` es una estructura y no tiene una clase base.  
  
 El marco de trabajo crea un objeto de `CPrintInfo` cada vez que elija el comando de impresión o de la vista previa de impresión y se destruye cuando se completa el comando.  
  
 `CPrintInfo` contiene información sobre el trabajo de impresión en conjunto, por ejemplo el intervalo de páginas de ser impreso, y el estado actual del trabajo de impresión, como la página que está impresa actualmente.  Alguna información se almacena en un objeto asociado de [CPrintDialog](../../mfc/reference/cprintdialog-class.md) ; este objeto contiene los valores especificados por el usuario en el cuadro de diálogo imprimir.  
  
 Un objeto de `CPrintInfo` se pasa entre el marco y la clase de vista durante el proceso de impresión y se utiliza para intercambiar información entre los dos.  Por ejemplo, el marco informa a la clase de vista qué página de documento a imprimir asignando un valor al miembro de `m_nCurPage` de `CPrintInfo`; la clase de vista recupera el valor y realiza la impresión real de la página especificada.  
  
 Otro ejemplo es el caso en el que la longitud del documento no se conoce hasta que se imprima.  En esta situación, las pruebas de clase de vista para el final del documento cada vez que se imprime una página.  Cuando se alcanza el final, la clase de vista establezca el miembro de `m_bContinuePrinting` de `CPrintInfo` a **FALSE**; esto indica al marco para detener el bucle de impresión.  
  
 `CPrintInfo` usa el miembro que las funciones de `CView` enumeradas bajo “vea Vea.” Para obtener más información sobre la arquitectura de impresión proporcionada por la biblioteca Microsoft Foundation Class, vea [cuadro Windows](../../mfc/frame-windows.md) y [Arquitectura documento\/vista](../../mfc/document-view-architecture.md) y los casos [el imprimir](../../mfc/printing.md) y [La impresión: Documentos de varias páginas](../../mfc/multipage-documents.md).  
  
## Jerarquía de herencia  
 `CPrintInfo`  
  
## Requisitos  
 **encabezado:** afxext.h  
  
## Vea también  
 [ejemplo DIBLOOK de MFC](../../top/visual-cpp-samples.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CView::OnBeginPrinting](../Topic/CView::OnBeginPrinting.md)   
 [CView::OnEndPrinting](../Topic/CView::OnEndPrinting.md)   
 [CView::OnEndPrintPreview](../Topic/CView::OnEndPrintPreview.md)   
 [CView::OnPrepareDC](../Topic/CView::OnPrepareDC.md)   
 [CView::OnPreparePrinting](../Topic/CView::OnPreparePrinting.md)   
 [CView::OnPrint](../Topic/CView::OnPrint.md)