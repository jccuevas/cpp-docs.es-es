---
title: Ver clases (arquitectura) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.view
dev_langs:
- C++
helpviewer_keywords:
- form and record views [MFC]
- view classes [MFC]
- control views [MFC]
- view classes [MFC], architecture
ms.assetid: 8894579a-1436-441e-b985-83711061e495
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 11bb3d9e551089a156d255f7b27fb55cbe87bdbe
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="view-classes-architecture"></a>Clases de vistas (Arquitectura)
`CView` y sus clases derivadas son ventanas secundarias que representan el área cliente de una ventana de marco. Vistas muestran los datos y aceptan la entrada de un documento.  
  
 Una clase de vista está asociada a una clase de documento y una clase de ventana de marco utilizando un objeto de plantilla de documento.  
  
 [CView](../mfc/reference/cview-class.md)  
 La clase base para las vistas específicas de la aplicación de datos de un documento. Vistas de mostrar datos y aceptan la entrada de usuario para editar o seleccionar los datos. Derive la clase o clases de vista de `CView`.  
  
 [CScrollView](../mfc/reference/cscrollview-class.md)  
 La clase base para las vistas con capacidades de desplazamiento. Derive la clase de vista de `CScrollView` para el desplazamiento automático.  
  
## <a name="form-and-record-views"></a>Formulario y vistas de registros  
 Vistas de formulario también desplacen vistas. Se basan en una plantilla de cuadro de diálogo.  
  
 Vistas de registros se derivan de vistas de formulario. Además de la plantilla de cuadro de diálogo, también tienen una conexión a una base de datos.  
  
 [CFormView](../mfc/reference/cformview-class.md)  
 Una vista de desplazamiento cuyo diseño está definido en una plantilla de cuadro de diálogo. Derivar una clase de `CFormView` para implementar una interfaz de usuario basada en una plantilla de cuadro de diálogo.  
  
 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md)  
 Proporciona una forma Vista conectada directamente a un objeto de conjunto de registros de objetos de acceso a datos (DAO). Al igual que todas las vistas de formulario y un `CDaoRecordView` se basa en una plantilla de cuadro de diálogo.  
  
 [CHtmlView](../mfc/reference/chtmlview-class.md)  
 Admite un control para la exploración Web dentro de una aplicación. El control admite HTML dinámico en MFC.  
  
 [COLEDBRecordView](../mfc/reference/coledbrecordview-class.md)  
 Proporciona compatibilidad con MFC OLE DB para vistas de formulario.  
  
 [CRecordView](../mfc/reference/crecordview-class.md)  
 Proporciona una forma Vista conectada directamente a un objeto de conjunto de registros de Open Database Connectivity (ODBC). Al igual que todas las vistas de formulario y un `CRecordView` se basa en una plantilla de cuadro de diálogo.  
  
## <a name="control-views"></a>Vistas de control  
 Vistas de control mostrar un control como su vista.  
  
 [CCtrlView](../mfc/reference/cctrlview-class.md)  
 La clase base para todas las vistas asociadas con los controles de Windows. Las vistas en función de los controles se describen a continuación.  
  
 [CEditView](../mfc/reference/ceditview-class.md)  
 Control de edición de una vista que contiene un estándar de Windows (consulte [CEdit](../mfc/reference/cedit-class.md)). Editar controles admiten texto la edición, buscar, reemplazar y capacidades de desplazamiento.  
  
 [CRichEditView](../mfc/reference/cricheditview-class.md)  
 Control de edición de una vista que contiene un completo de Windows (consulte [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Además de las capacidades de un control de edición, rich edit controles compatibilidad con fuentes, colores, el formato de párrafo y objetos OLE incrustados.  
  
 [CListView](../mfc/reference/clistview-class.md)  
 Una vista que contiene un control de lista de Windows (consulte [CListCtrl](../mfc/reference/clistctrl-class.md)). Un control de lista muestra los iconos y las cadenas de una manera similar en el panel derecho del explorador de archivos.  
  
 [CTreeView](../mfc/reference/ctreeview-class.md)  
 Una vista que contiene un control de árbol de Windows (consulte [CTreeCtrl](../mfc/reference/ctreectrl-class.md)). Un control de árbol muestra iconos y cadenas que se organizan en una jerarquía de una manera similar al panel izquierdo del explorador de archivos.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../mfc/class-library-overview.md)

