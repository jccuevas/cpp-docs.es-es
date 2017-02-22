---
title: "Estilos utilizados por MFC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.styles"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "botones, barras de herramientas de MFC"
  - "cuadros combinados, estilos"
  - "estilos de edición [MFC]"
  - "estilos de ventana extendidos"
  - "ventanas de marco, estilos"
  - "cuadros de lista, estilos"
  - "estilos de cuadro de mensaje"
  - "estilos de barra de desplazamiento [MFC]"
  - "estilos estáticos"
  - "estilos"
  - "estilos, MFC"
  - "estilos de ventanas, en MFC"
ms.assetid: d3b9af37-31b5-4c97-a8ad-189fd724b04c
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# Estilos utilizados por MFC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Utilice los estilos siguientes cuando se crea el objeto correspondiente de MFC.  En la mayoría de los casos, estos estilos se establecen en el parámetro de `dwStyle` de la función de **crear** de la clase.  
  
### Estilos de MFC  
  
|Estilo|Descripción|  
|------------|-----------------|  
|[Estilos de botón](../../mfc/reference/button-styles.md)|Se aplica a los objetos de [Clase de CButton](../../mfc/reference/cbutton-class.md) , como botones de radio, casillas y pulsadores.  Especifique una combinación de los estilos en el parámetro de `dwStyle` de [CButton::Create](../Topic/CButton::Create.md).|  
|[Estilos de cuadro combinado](../../mfc/reference/combo-box-styles.md)|Se aplica a los objetos de [Clase CComboBox](../../mfc/reference/ccombobox-class.md) .  Especifique una combinación de los estilos en el parámetro de `dwStyle` de [CComboBox::Create](../Topic/CComboBox::Create.md).|  
|[Edite los estilos](../../mfc/reference/edit-styles.md)|Se aplica a los objetos de [Clase de CEdit](../../mfc/reference/cedit-class.md) .  Especifique una combinación de los estilos en el parámetro de `dwStyle` de [CEdit::Create](../Topic/CEdit::Create.md).|  
|[Estilos de la Cuadro\-ventana](../../mfc/reference/frame-window-styles-mfc.md)|Se aplica a los objetos de [Clase CFrameWnd](../../mfc/reference/cframewnd-class.md) .  Especifique una combinación de los estilos en el parámetro de `dwStyle` de [CFrameWnd::Create](../Topic/CFrameWnd::Create.md).|  
|[Estilos de listbox](../../mfc/reference/list-box-styles.md)|Se aplica a los objetos de [Clase de CListBox](../../mfc/reference/clistbox-class.md) .  Especifique una combinación de los estilos en el parámetro de `dwStyle` de [CListBox::Create](../Topic/CListBox::Create.md).|  
|[Estilos de cuadro de mensaje](../../mfc/reference/message-box-styles.md)|Se aplica a los elementos de [AfxMessageBox](../Topic/AfxMessageBox.md) .  Especifique una combinación de los estilos en el parámetro de `nType` de `AfxMessageBox`.|  
|[Estilos de scrollbar](../../mfc/reference/scroll-bar-styles.md)|Se aplica a los objetos de [Clase de CScrollBar](../../mfc/reference/cscrollbar-class.md) .  Especifique una combinación de los estilos en el parámetro de `dwStyle` de [CScrollBar::Create](../Topic/CScrollBar::Create.md).|  
|[Estilos estáticos](../../mfc/reference/static-styles.md)|Se aplica a los objetos de [Clase de CStatic](../../mfc/reference/cstatic-class.md) .  Especifique una combinación de los estilos en el parámetro de `dwStyle` de [CStatic::Create](../Topic/CStatic::Create.md).|  
|[Estilos de ventana](../../mfc/reference/window-styles.md)|Se aplica a los objetos de [Clase de CWnd](../../mfc/reference/cwnd-class.md) .  Especifique una combinación de los estilos en el parámetro de `dwStyle` de [CWnd::Create](../Topic/CWnd::Create.md) o de [CWnd::CreateEx](../Topic/CWnd::CreateEx.md).|  
|[Estilos de ventana extendidas](../../mfc/reference/extended-window-styles.md)|Se aplica a los objetos de [Clase de CWnd](../../mfc/reference/cwnd-class.md) .  Especifique una combinación de los estilos en el parámetro de `dwExStyle` de [CWnd::CreateEx](../Topic/CWnd::CreateEx.md).|  
  
## Vea también  
 [Información general de clases](../../mfc/class-library-overview.md)