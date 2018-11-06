---
title: Clases de vistas derivadas disponibles en MFC
ms.date: 11/04/2016
helpviewer_keywords:
- CView class [MFC], classes derived from
- classes [MFC], derived
- derived classes [MFC], view classes
- view classes [MFC], derived
ms.assetid: dba42178-7459-4ccc-b025-f3d9b8a4b737
ms.openlocfilehash: 9972586bd0cc4059e81d81be954a8cf0cada1f0d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594510"
---
# <a name="derived-view-classes-available-in-mfc"></a>Clases de vistas derivadas disponibles en MFC

La siguiente tabla muestra las clases de vista de MFC y sus relaciones entre sí. Las capacidades de la clase de vista dependen del que se deriva la clase de vista MFC.

### <a name="view-classes"></a>Clases de vistas

|Clase|Descripción|
|-----------|-----------------|
|[CView](../mfc/reference/cview-class.md)|Clase base de todas las vistas.|
|[CCtrlView](../mfc/reference/cctrlview-class.md)|Clase de base `CTreeView`, `CListView`, `CEditView`, y `CRichEditView`. Estas clases le permiten usar la arquitectura documento/vista con los controles comunes de Windows indicados.|
|[CEditView](../mfc/reference/ceditview-class.md)|Una vista sencilla basada en el Windows editar control de cuadro. Permite escribir y editar texto y puede usarse como base para una aplicación de editor de texto simple. Vea también `CRichEditView`.|
|[CRichEditView](../mfc/reference/cricheditview-class.md)|Una vista que contiene un [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) objeto. Esta clase es análoga a `CEditView`, pero a diferencia `CEditView`, `CRichEditView` controla texto con formato.|
|[CListView](../mfc/reference/clistview-class.md)|Una vista que contiene un [CListCtrl](../mfc/reference/clistctrl-class.md) objeto.|
|[CTreeView](../mfc/reference/ctreeview-class.md)|Una vista que contiene un [CTreeCtrl](../mfc/reference/ctreectrl-class.md) objeto, para las vistas que son similares a la ventana Explorador de soluciones en Visual C++.|
|[CScrollView](../mfc/reference/cscrollview-class.md)|Clase de base `CFormView`, `CRecordView`, y `CDaoRecordView`. Implementa el contenido de la vista de desplazamiento.|
|[CFormView](../mfc/reference/cformview-class.md)|Una vista de formulario, una vista que contiene los controles. Una aplicación basada en formularios proporciona una o varias de estas interfaces de formulario.|
|[CHtmlView](../mfc/reference/chtmlview-class.md)|Una vista de explorador Web con la que los usuarios de la aplicación pueden examinar sitios en el World Wide Web, así como carpetas en el sistema de archivos local y en una red. La vista de explorador Web también puede funcionar como un contenedor de documentos activos.|
|[CRecordView](../mfc/reference/crecordview-class.md)|Una vista de formulario que muestra registros de base de datos ODBC en controles. Si selecciona la compatibilidad ODBC en el proyecto, la clase de base de la vista es `CRecordView`. La vista está conectada a un `CRowset` objeto.|
|[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)|Una vista de formulario que muestra registros de base de datos DAO en controles. Si selecciona la compatibilidad DAO en el proyecto, la clase de base de la vista es `CDaoRecordView`. La vista está conectada a un `CDaoRecordset` objeto.|
|[COleDBRecordView](../mfc/reference/coledbrecordview-class.md)|Una vista de formulario que muestra registros de OLE DB en controles. Si selecciona compatibilidad con OLE DB en el proyecto, la clase de base de la vista es `COleDBRecordView`. La vista está conectada a un `CRowset` objeto.|

> [!NOTE]
>  A partir de la versión 4.0, MFC `CEditView` se deriva de `CCtrlView`.

Para utilizar estas clases en la aplicación, derivar las clases de vista de la aplicación de ellos. Para obtener información relacionada, consulte [desplazamiento y escalar vistas](../mfc/scrolling-and-scaling-views.md). Para obtener más información sobre las clases de base de datos, vea [información general: programación de base de datos](../data/data-access-programming-mfc-atl.md).

## <a name="see-also"></a>Vea también

[Uso de vistas](../mfc/using-views.md)

