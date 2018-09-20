---
title: Ver las clases (Windows) | Microsoft Docs
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
- splitter window classes [MFC]
- view classes [MFC], Windows
ms.assetid: b11683fb-9f43-4de3-9499-2b55775f9870
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b347fcc14b477ab83a3bc0b6dfa2c0c80adeb791
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428881"
---
# <a name="view-classes-windows"></a>Clases de vistas (Windows)

`CView` y sus clases derivadas son ventanas secundarias que representan el área cliente de una ventana de marco. Las vistas muestran los datos y aceptan la entrada de un documento.

Una clase de vista se asocia con una clase de documento y una clase de ventana de marco utilizando un objeto de plantilla de documento.

[CView](../mfc/reference/cview-class.md)<br/>
La clase base para las vistas específicas de la aplicación de datos de un documento. Vistas de mostrarán los datos y aceptan la entrada de usuario para editar o seleccione los datos. Derive la clase de vista o clases de `CView`.

[CScrollView](../mfc/reference/cscrollview-class.md)<br/>
La clase base para las vistas con capacidades de desplazamiento. Derive la clase de vista de `CScrollView` para el desplazamiento automático.

## <a name="form-and-record-views"></a>Formulario y las vistas de registros

Las vistas de formulario también desplaza las vistas. Se basan en una plantilla de cuadro de diálogo.

Vistas de registros se derivan de las vistas de formulario. Además de la plantilla de cuadro de diálogo también tienen una conexión a una base de datos.

[CFormView](../mfc/reference/cformview-class.md)<br/>
Una vista de desplazamiento cuyo diseño se define en una plantilla de cuadro de diálogo. Derive una clase de `CFormView` para implementar una interfaz de usuario basada en una plantilla de cuadro de diálogo.

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
Proporciona un formulario de vista directamente conectada a un objeto de conjunto de registros de objeto de acceso a datos (DAO). Al igual que todas las vistas de formulario, un `CDaoRecordView` se basa en una plantilla de cuadro de diálogo.

[CRecordView](../mfc/reference/crecordview-class.md)<br/>
Proporciona un formulario de vista directamente conectada a un objeto de conjunto de registros de Open Database Connectivity (ODBC). Al igual que todas las vistas de formulario, un `CRecordView` se basa en una plantilla de cuadro de diálogo.

[CHtmlEditView](../mfc/reference/chtmleditview-class.md)<br/>
Una vista de formulario que proporciona la funcionalidad de la plataforma de edición WebBrowser HTML.

## <a name="control-views"></a>Vistas de control

Vistas de control muestran un control como su vista.

[CCtrlView](../mfc/reference/cctrlview-class.md)<br/>
La clase base para todas las vistas asociadas con los controles de Windows. Las vistas en función de los controles se describen a continuación.

[CEditView](../mfc/reference/ceditview-class.md)<br/>
Control de edición de una vista que contiene un estándar de Windows (consulte [CEdit](../mfc/reference/cedit-class.md)). Editar la edición de texto de soporte técnico de los controles, buscar, reemplazar y capacidades de desplazamiento.

[CRichEditView](../mfc/reference/cricheditview-class.md)<br/>
Control de edición de una vista que contiene un completo de Windows (consulte [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Además de las capacidades de un control de edición, enriquecido editar controles compatibilidad con fuentes, colores, el formato de párrafo y objetos OLE incrustados.

[CListView](../mfc/reference/clistview-class.md)<br/>
Una vista que contiene un control de lista de Windows (consulte [CListCtrl](../mfc/reference/clistctrl-class.md)). Un control de lista muestra una colección de elementos, cada uno de los que consta de un icono y una etiqueta, de manera similar en el panel derecho del explorador de archivos.

[CTreeView](../mfc/reference/ctreeview-class.md)<br/>
Una vista que contiene un control de árbol de Windows (consulte [CTreeCtrl](../mfc/reference/ctreectrl-class.md)). Un control de árbol muestra una lista jerárquica de los iconos y las etiquetas que se organizan de forma similar al panel izquierdo del explorador de archivos.

## <a name="related-classes"></a>Clases relacionadas

`CSplitterWnd` le permite tener varias vistas dentro de una sola ventana de marco. `CPrintDialog` y `CPrintInfo` admiten la capacidad de impresión y la vista preliminar de las vistas. `CRichEditDoc` y `CRichEditCntrItem` se usan con `CRichEditView` para implementar capacidades de contenedor OLE.

[CSplitterWnd](../mfc/reference/csplitterwnd-class.md)<br/>
Una ventana que el usuario puede dividir en varios paneles. Estos paneles pueden ser redimensionables por el usuario o un tamaño fijo.

[CPrintDialog](../mfc/reference/cprintdialog-class.md)<br/>
Proporciona un cuadro de diálogo estándar para imprimir un archivo.

[CPrintInfo](../mfc/reference/cprintinfo-structure.md)<br/>
Una estructura que contiene información acerca de un trabajo de impresión o vista preliminar. Utilizado por `CView`de impresión de arquitectura.

[CRichEditDoc](../mfc/reference/cricheditdoc-class.md)<br/>
Mantiene la lista de elementos de cliente OLE que se encuentran en un `CRichEditView`.

[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)<br/>
Proporciona acceso de cliente a OLE elementos almacenado en un `CRichEditView`.

## <a name="see-also"></a>Vea también

[Información general de clases](../mfc/class-library-overview.md)

