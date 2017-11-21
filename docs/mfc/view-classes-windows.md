---
title: Ver clases (Windows) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.view
dev_langs: C++
helpviewer_keywords:
- form and record views [MFC]
- splitter window classes [MFC]
- view classes [MFC], Windows
ms.assetid: b11683fb-9f43-4de3-9499-2b55775f9870
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0148ead7a978389f763efbe9ee6306ec7a5839cd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="view-classes-windows"></a>Clases de vistas (Windows)
`CView`y sus clases derivadas son ventanas secundarias que representan el área cliente de una ventana de marco. Vistas muestran los datos y aceptan la entrada de un documento.  
  
 Una clase de vista está asociada a una clase de documento y una clase de ventana de marco utilizando un objeto de plantilla de documento.  
  
 [CView](../mfc/reference/cview-class.md)  
 La clase base para las vistas específicas de la aplicación de datos de un documento. Vistas de mostrar datos y aceptan la entrada de usuario para editar o seleccionar los datos. Derive la clase de vista o clases de `CView`.  
  
 [CScrollView](../mfc/reference/cscrollview-class.md)  
 La clase base para las vistas con capacidades de desplazamiento. Derive la clase de vista de `CScrollView` para el desplazamiento automático.  
  
## <a name="form-and-record-views"></a>Formulario y vistas de registros  
 Vistas de formulario también desplacen vistas. Se basan en una plantilla de cuadro de diálogo.  
  
 Vistas de registros se derivan de vistas de formulario. Además de la plantilla de cuadro de diálogo, también tienen una conexión a una base de datos.  
  
 [CFormView](../mfc/reference/cformview-class.md)  
 Una vista de desplazamiento cuyo diseño está definido en una plantilla de cuadro de diálogo. Derivar una clase de `CFormView` para implementar una interfaz de usuario basada en una plantilla de cuadro de diálogo.  
  
 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md)  
 Proporciona una forma Vista conectada directamente a un objeto de conjunto de registros de objetos de acceso a datos (DAO). Al igual que todas las vistas de formulario y un `CDaoRecordView` se basa en una plantilla de cuadro de diálogo.  
  
 [CRecordView](../mfc/reference/crecordview-class.md)  
 Proporciona una forma Vista conectada directamente a un objeto de conjunto de registros de Open Database Connectivity (ODBC). Al igual que todas las vistas de formulario y un `CRecordView` se basa en una plantilla de cuadro de diálogo.  
  
 [CHtmlEditView](../mfc/reference/chtmleditview-class.md)  
 Una vista de formulario que proporciona la funcionalidad de la plataforma de edición WebBrowser HTML.  
  
## <a name="control-views"></a>Vistas de control  
 Vistas de control mostrar un control como su vista.  
  
 [CCtrlView](../mfc/reference/cctrlview-class.md)  
 La clase base para todas las vistas asociadas con los controles de Windows. Las vistas en función de los controles se describen a continuación.  
  
 [CEditView](../mfc/reference/ceditview-class.md)  
 Control de edición de una vista que contiene un estándar de Windows (consulte [CEdit](../mfc/reference/cedit-class.md)). Editar controles admiten texto la edición, buscar, reemplazar y capacidades de desplazamiento.  
  
 [CRichEditView](../mfc/reference/cricheditview-class.md)  
 Control de edición de una vista que contiene un completo de Windows (consulte [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Además de las capacidades de un control de edición, rich edit controles compatibilidad con fuentes, colores, el formato de párrafo y objetos OLE incrustados.  
  
 [CListView](../mfc/reference/clistview-class.md)  
 Una vista que contiene un control de lista de Windows (consulte [CListCtrl](../mfc/reference/clistctrl-class.md)). Un control de lista muestra una colección de elementos, cada uno de los que se compone de un icono y una etiqueta, de forma similar en el panel derecho del explorador de archivos.  
  
 [CTreeView](../mfc/reference/ctreeview-class.md)  
 Una vista que contiene un control de árbol de Windows (consulte [CTreeCtrl](../mfc/reference/ctreectrl-class.md)). Un control de árbol muestra una lista jerárquica de los iconos y etiquetas organizadas de forma similar al panel izquierdo del explorador de archivos.  
  
## <a name="related-classes"></a>Clases relacionadas  
 `CSplitterWnd`le permite tener varias vistas dentro de una sola ventana de marco. `CPrintDialog`y `CPrintInfo` admiten la capacidad de impresión y la vista preliminar de vistas. `CRichEditDoc`y `CRichEditCntrItem` se usan con `CRichEditView` para implementar capacidades de contenedor OLE.  
  
 [CSplitterWnd](../mfc/reference/csplitterwnd-class.md)  
 Una ventana que el usuario puede dividir en varios paneles. Estos paneles se puede cambiar el tamaño por el usuario o un tamaño fijo.  
  
 [CPrintDialog](../mfc/reference/cprintdialog-class.md)  
 Proporciona un cuadro de diálogo estándar para imprimir un archivo.  
  
 [CPrintInfo](../mfc/reference/cprintinfo-structure.md)  
 Una estructura que contiene información acerca de un trabajo de impresión o vista preliminar. Utilizado por `CView`de la arquitectura de impresión.  
  
 [CRichEditDoc](../mfc/reference/cricheditdoc-class.md)  
 Mantiene la lista de elementos de cliente OLE que se encuentran en un `CRichEditView`.  
  
 [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)  
 Proporciona acceso de cliente a un OLE elementos almacenado en un `CRichEditView`.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../mfc/class-library-overview.md)

