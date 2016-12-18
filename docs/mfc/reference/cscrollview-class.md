---
title: "CScrollView Class | Microsoft Docs"
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
  - "CScrollView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CScrollView class"
  - "scrolling views"
  - "vistas, desplazarse"
ms.assetid: 4ba16dac-1acb-4be0-bb55-5fb695b6948d
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CScrollView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[CView](../../mfc/reference/cview-class.md) con capacidades de desplazamiento.  
  
## Sintaxis  
  
```  
class CScrollView : public CView  
```  
  
## Miembros  
  
### Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CScrollView::CScrollView](../Topic/CScrollView::CScrollView.md)|Crea un objeto `CScrollView`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CScrollView::CheckScrollBars](../Topic/CScrollView::CheckScrollBars.md)|Indica si la vista de desplazamiento tiene barras de desplazamiento horizontal y vertical.|  
|[CScrollView::FillOutsideRect](../Topic/CScrollView::FillOutsideRect.md)|Rellena el área de una vista fuera del área que se mueve.|  
|[CScrollView::GetDeviceScrollPosition](../Topic/CScrollView::GetDeviceScrollPosition.md)|Obtiene la posición de desplazamiento actual en unidades.|  
|[CScrollView::GetDeviceScrollSizes](../Topic/CScrollView::GetDeviceScrollSizes.md)|Obtiene el modo actual de asignación, el tamaño total, y la línea y tamaños de página de vista desplazable.  Los tamaños están en unidades.|  
|[CScrollView::GetScrollPosition](../Topic/CScrollView::GetScrollPosition.md)|Obtiene la posición de desplazamiento actual en unidades lógicas.|  
|[CScrollView::GetTotalSize](../Topic/CScrollView::GetTotalSize.md)|Obtiene el tamaño total de la vista de desplazamiento en unidades lógicas.|  
|[CScrollView::ResizeParentToFit](../Topic/CScrollView::ResizeParentToFit.md)|Hace que el tamaño de la vista para dictar el tamaño del marco.|  
|[CScrollView::ScrollToPosition](../Topic/CScrollView::ScrollToPosition.md)|Desplaza la vista en un momento determinado, especificado en unidades lógicas.|  
|[CScrollView::SetScaleToFitSize](../Topic/CScrollView::SetScaleToFitSize.md)|Coloca la vista de desplazamiento en modo de escala\-a\- ajuste.|  
|[CScrollView::SetScrollSizes](../Topic/CScrollView::SetScrollSizes.md)|Establece el modo de asignación de la vista de desplazamiento, tamaño total, y el desplazamiento horizontal y vertical promueve.|  
  
## Comentarios  
 Puede controlar desplazamiento rápido manualmente en cualquier clase derivada de `CView` reemplazando [OnHScroll](../Topic/CWnd::OnHScroll.md) mensaje\- asignado y el miembro de [OnVScroll](../Topic/CWnd::OnVScroll.md) funciona.  Pero `CScrollView` agrega las siguientes características para sus capacidades de `CView` :  
  
-   Administra los tamaños de la ventana y de la ventanilla y los modos de asignación.  
  
-   Desplaza automáticamente en respuesta a los mensajes de la barra de desplazamiento.  
  
-   Desplaza automáticamente en respuesta a los mensajes del teclado, de un mouse de no de desplazamiento, o la rueda de IntelliMouse.  
  
 Para desplazarse automáticamente en respuesta a los mensajes del teclado, agregar un mensaje WM\_KEYDOWN, y pruebas para VK\_DOWN, VK\_PREV y la llamada [SetScrollPos](http://msdn.microsoft.com/library/windows/desktop/bb787597).  
  
 Puede controlar el desplazamiento de la rueda del mouse personalmente reemplazando [OnMouseWheel](../Topic/CWnd::OnMouseWheel.md) mensaje\- asignado y el miembro de [OnRegisteredMouseWheel](../Topic/CWnd::OnRegisteredMouseWheel.md) funciona.  Mientras se para `CScrollView`, estas funciones miembro admiten el comportamiento recomendado para [WM\_MOUSEWHEEL](http://msdn.microsoft.com/library/windows/desktop/ms645617), el mensaje de rotación de la rueda.  
  
 Para aprovecharse de desplazamiento automático, derive la clase de vista de `CScrollView` en lugar de `CView`.  Cuando la vista se crea por primera vez, si desea calcular el tamaño de la vista desplazable basada en el tamaño del documento, llame a la función miembro de `SetScrollSizes` de la invalidación de [CView::OnInitialUpdate](../Topic/CView::OnInitialUpdate.md) o de [CView::OnUpdate](../Topic/CView::OnUpdate.md).  \(Debe escribir su propio código para ver el tamaño del documento.  Para obtener un ejemplo, vea [Scribble el ejemplo](../../top/visual-cpp-samples.md).\)  
  
 La llamada a la función miembro de `SetScrollSizes` establece el modo de asignación de la vista, las dimensiones totales de la vista de desplazamiento, y los importes para desplazarse horizontal y verticalmente.  Todos los tamaños están en unidades lógicas.  El tamaño lógico de la vista se calcula general de los datos almacenados en el documento, pero quizá desee en algunos casos para especificar un tamaño fijo.  Para obtener ejemplos de ambos enfoques, vea [CScrollView::SetScrollSizes](../Topic/CScrollView::SetScrollSizes.md).  
  
 Especifica los importes para desplazarse horizontal y verticalmente en unidades lógicas.  De forma predeterminada, si el usuario hace clic en un eje de la barra de desplazamiento fuera del cuadro de desplazamiento, `CScrollView` desplaza una “página”. Si el usuario hace clic en una flecha de desplazamiento en final de una barra de desplazamiento, `CScrollView` desplaza una “línea”. De forma predeterminada, una página es 1\/10 del tamaño total de la vista; una línea es 1\/10 de tamaño de página.  Invalide estos valores predeterminados pasando los tamaños personalizados en la función miembro de `SetScrollSizes` .  Por ejemplo, puede establecer el tamaño horizontal a alguna fracción del ancho del tamaño total y el tamaño vertical al alto de una línea de la fuente actual.  
  
 En lugar de desplazamiento, `CScrollView` puede ajustar automáticamente la escala de la vista al tamaño de la ventana actual.  En este modo, la vista no tiene ninguna barra de desplazamiento y la vista lógica se ajusta o se reduce para ajustarse exactamente el área cliente de la ventana.  Para utilizar esta capacidad de escala\-a\- ajuste, llame a [CScrollView::SetScaleToFitSize](../Topic/CScrollView::SetScaleToFitSize.md).  \(Llame a `SetScaleToFitSize` o `SetScrollSizes`, pero no ambos\).  
  
 Antes de que la función miembro de `OnDraw` de su clase derivada de la vista se denomina, `CScrollView` incluye automáticamente al origen del área de visualización para el objeto de dispositivo\- contexto de `CPaintDC` que pasa a `OnDraw`.  
  
 Para ajustar el origen de la ventanilla para la ventana de desplazamiento, `CScrollView` reemplaza [CView::OnPrepareDC](../Topic/CView::OnPrepareDC.md).  Este ajuste es automático para el contexto del dispositivo de `CPaintDC` que `CScrollView` pasa a `OnDraw`, pero debe llamar a **CScrollView::OnPrepareDC** a para cualquier otro contexto de dispositivo que se utilice, por ejemplo `CClientDC`.  Puede reemplazar **CScrollView::OnPrepareDC** para establecer el lápiz, el color de fondo, y otros atributos del gráfico, pero llama a la clase base para realizar el ajuste de escala.  
  
 Las barras de desplazamiento pueden aparecer en tres lugares en relación con una vista, como se muestra en los siguientes casos:  
  
-   Las barras de desplazamiento estándar de estilo de ventana se pueden establecer para la vista mediante **WS\_HSCROLL** y **WS\_VSCROLL**[estilos de Windows](../../mfc/reference/window-styles.md).  
  
-   Los controles de barra de desplazamiento también se pueden agregar al cuadro que contiene la vista, en cuyo caso el marco reenvía `WM_HSCROLL` y los mensajes de `WM_VSCROLL` de la ventana de marco a la vista activa.  
  
-   El marco de trabajo también reenvía mensajes de desplazamiento de un control splitter de `CSplitterWnd` actualmente el panel activo splitter \(una vista\).  Cuando se coloca en [CSplitterWnd](../../mfc/reference/csplitterwnd-class.md) con las barras de desplazamiento compartidas, un objeto de `CScrollView` utilizará compartidos en lugar de crear su propio.  
  
 Para obtener más información sobre cómo utilizar `CScrollView`, vea [Arquitectura documento\/vista](../../mfc/document-view-architecture.md) y [La vista derivada ordena disponibles en MFC](../../mfc/derived-view-classes-available-in-mfc.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 `CScrollView`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [ejemplo DIBLOOK de MFC](../../top/visual-cpp-samples.md)   
 [CView Class](../../mfc/reference/cview-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CView Class](../../mfc/reference/cview-class.md)   
 [CSplitterWnd Class](../../mfc/reference/csplitterwnd-class.md)