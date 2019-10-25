---
title: Clases de vistas (Windows)
ms.date: 09/17/2019
f1_keywords:
- vc.classes.view
helpviewer_keywords:
- form and record views [MFC]
- splitter window classes [MFC]
- view classes [MFC], Windows
ms.assetid: b11683fb-9f43-4de3-9499-2b55775f9870
ms.openlocfilehash: f3e9ea2ebf3eb0ce04fde0339aaf0243686248a9
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2019
ms.locfileid: "71096040"
---
# <a name="view-classes-windows"></a>Clases de vistas (Windows)

`CView`y sus clases derivadas son ventanas secundarias que representan el área de cliente de una ventana de marco. Las vistas muestran datos y aceptan entradas para un documento.

Una clase de vista se asocia a una clase de documento y una clase de ventana de marco mediante un objeto de plantilla de documento.

[CView](../mfc/reference/cview-class.md)<br/>
La clase base para las vistas específicas de la aplicación de los datos de un documento. Las vistas muestran datos y aceptan la entrada del usuario para editar o seleccionar los datos. Derive la clase o clases de vista `CView`de.

[CScrollView](../mfc/reference/cscrollview-class.md)<br/>
Clase base para las vistas con capacidades de desplazamiento. Derive la clase de vista `CScrollView` de para el desplazamiento automático.

## <a name="form-and-record-views"></a>Vistas de formulario y de registros

Las vistas de formulario también se desplazan por las vistas. Se basan en una plantilla de cuadro de diálogo.

Las vistas de registros se derivan de las vistas de formulario. Además de la plantilla de cuadro de diálogo, también tienen una conexión a una base de datos.

[CFormView](../mfc/reference/cformview-class.md)<br/>
Vista de desplazamiento cuyo diseño se define en una plantilla de cuadro de diálogo. Derive una clase de `CFormView` para implementar una interfaz de usuario basada en una plantilla de cuadro de diálogo.

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
Proporciona una vista de formulario conectada directamente a un objeto de conjunto de registros de objetos de acceso a datos (DAO). Al igual que todas las vistas `CDaoRecordView` de formulario, se basa en una plantilla de cuadro de diálogo. DAO se utiliza con bases de datos de Access y se admite a través de Office 2013. 3,6 es la versión final y se considera obsoleta.

[CRecordView](../mfc/reference/crecordview-class.md)<br/>
Proporciona una vista de formulario conectada directamente a un objeto de conjunto de registros ODBC (Conectividad abierta de bases de datos). Al igual que todas las vistas `CRecordView` de formulario, se basa en una plantilla de cuadro de diálogo.

[CHtmlEditView](../mfc/reference/chtmleditview-class.md)<br/>
Una vista de formulario que proporciona la funcionalidad de la plataforma de edición HTML de WebBrowser.

## <a name="control-views"></a>Vistas de control

Las vistas de control muestran un control como su vista.

[CCtrlView](../mfc/reference/cctrlview-class.md)<br/>
La clase base para todas las vistas asociadas a controles de Windows. A continuación se describen las vistas basadas en controles.

[CEditView](../mfc/reference/ceditview-class.md)<br/>
Una vista que contiene un control de edición estándar de Windows (vea [CEDIT](../mfc/reference/cedit-class.md)). Los controles de edición admiten funciones de edición de texto, búsqueda, reemplazo y desplazamiento.

[CRichEditView](../mfc/reference/cricheditview-class.md)<br/>
Una vista que contiene un control Rich Edit de Windows (vea [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Además de las capacidades de un control de edición, los controles Rich Edit admiten fuentes, colores, formato de párrafo y objetos OLE incrustados.

[CListView](../mfc/reference/clistview-class.md)<br/>
Una vista que contiene un control de lista de Windows (vea [CListCtrl](../mfc/reference/clistctrl-class.md)). Un control de lista muestra una colección de elementos, cada uno de los cuales consta de un icono y una etiqueta, de forma similar al panel derecho del explorador de archivos.

[CTreeView](../mfc/reference/ctreeview-class.md)<br/>
Una vista que contiene un control de árbol de Windows (vea [CTreeCtrl](../mfc/reference/ctreectrl-class.md)). Un control de árbol muestra una lista jerárquica de iconos y etiquetas organizadas de forma similar al panel izquierdo del explorador de archivos.

## <a name="related-classes"></a>Clases relacionadas

`CSplitterWnd`permite tener varias vistas en una sola ventana de marco. `CPrintDialog`y `CPrintInfo` admiten la capacidad de impresión y vista previa de impresión de las vistas. `CRichEditDoc`y `CRichEditCntrItem` se usan con `CRichEditView` para implementar capacidades de contenedor OLE.

[CSplitterWnd](../mfc/reference/csplitterwnd-class.md)<br/>
Ventana que el usuario puede dividir en varios paneles. El usuario o el tamaño fijo pueden cambiar el tamaño de estos paneles.

[CPrintDialog](../mfc/reference/cprintdialog-class.md)<br/>
Proporciona un cuadro de diálogo estándar para imprimir un archivo.

[CPrintInfo](../mfc/reference/cprintinfo-structure.md)<br/>
Estructura que contiene información sobre un trabajo de impresión o de vista previa de impresión. Usado por `CView`la arquitectura de impresión de.

[CRichEditDoc](../mfc/reference/cricheditdoc-class.md)<br/>
Mantiene la lista de elementos de cliente OLE que se encuentran `CRichEditView`en.

[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)<br/>
Proporciona acceso del lado cliente a un elemento OLE almacenado en un `CRichEditView`.

## <a name="see-also"></a>Vea también

[Información general sobre clases](../mfc/class-library-overview.md)
