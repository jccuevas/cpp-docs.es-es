---
title: Clases de vistas derivadas disponibles en MFC
ms.date: 11/04/2016
helpviewer_keywords:
- CView class [MFC], classes derived from
- classes [MFC], derived
- derived classes [MFC], view classes
- view classes [MFC], derived
ms.assetid: dba42178-7459-4ccc-b025-f3d9b8a4b737
ms.openlocfilehash: 12b31074e4fcc2ed6a83e3669e1044f5b9caedab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373502"
---
# <a name="derived-view-classes-available-in-mfc"></a>Clases de vistas derivadas disponibles en MFC

En la tabla siguiente se muestran las clases de vista de MFC y sus relaciones entre sí. Las capacidades de la clase de vista dependen de la clase de vista MFC de la que deriva.

### <a name="view-classes"></a>Ver clases

|Clase|Descripción|
|-----------|-----------------|
|[CView](../mfc/reference/cview-class.md)|Clase base de todas las vistas.|
|[CCtrlView](../mfc/reference/cctrlview-class.md)|Clase base `CTreeView` `CListView`de `CEditView`, `CRichEditView`, y . Estas clases le permiten utilizar la arquitectura de documento/vista con los controles comunes de Windows indicados.|
|[CEditView](../mfc/reference/ceditview-class.md)|Una vista simple basada en el control de cuadro de edición de Windows. Permite introducir y editar texto y se puede utilizar como base para una sencilla aplicación de editor de texto. Consulte también `CRichEditView`.|
|[CRichEditView](../mfc/reference/cricheditview-class.md)|Vista que contiene un objeto [CRichEditCtrl.](../mfc/reference/cricheditctrl-class.md) Esta clase es `CEditView`análoga a , pero a diferencia `CEditView`de , `CRichEditView` controla el texto con formato.|
|[CListView](../mfc/reference/clistview-class.md)|Una vista que contiene un [CListCtrl](../mfc/reference/clistctrl-class.md) objeto.|
|[CTreeView](../mfc/reference/ctreeview-class.md)|Una vista que contiene un [CTreeCtrl](../mfc/reference/ctreectrl-class.md) objeto, para vistas que se asemejan a la ventana Explorador de soluciones en Visual C++.|
|[CScrollView](../mfc/reference/cscrollview-class.md)|Clase base `CFormView` `CRecordView`de `CDaoRecordView`, , y . Implementa desplazar el contenido de la vista.|
|[CFormView](../mfc/reference/cformview-class.md)|Una vista de formulario, una vista que contiene controles. Una aplicación basada en formularios proporciona una o varias interfaces de formulario.|
|[CHtmlView](../mfc/reference/chtmlview-class.md)|Una vista del explorador web con la que el usuario de la aplicación puede examinar sitios en la World Wide Web, así como carpetas en el sistema de archivos local y en una red. La vista explorador web también puede funcionar como un contenedor de documentos activos.|
|[CRecordView](../mfc/reference/crecordview-class.md)|Vista de formulario que muestra registros de base de datos ODBC en controles. Si selecciona compatibilidad con ODBC en el proyecto, `CRecordView`la clase base de la vista es . La vista está `CRowset` conectada a un objeto.|
|[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)|Vista de formulario que muestra registros de base de datos DAO en controles. Si selecciona compatibilidad con DAO en el proyecto, `CDaoRecordView`la clase base de la vista es . La vista está `CDaoRecordset` conectada a un objeto.|
|[COleDBRecordView](../mfc/reference/coledbrecordview-class.md)|Vista de formulario que muestra registros OLE DB en controles. Si selecciona compatibilidad con OLE DB en el proyecto, la clase base de la vista es `COleDBRecordView`. La vista está `CRowset` conectada a un objeto.|

> [!NOTE]
> A partir de la `CEditView` versión 4.0 de MFC, se deriva de `CCtrlView`.

Para usar estas clases en la aplicación, derive las clases de vista de la aplicación de ellas. Para obtener información relacionada, consulte [Vistas de desplazamiento y escalado](../mfc/scrolling-and-scaling-views.md). Para obtener más información sobre las clases de base de datos, vea [Información general: Programación](../data/data-access-programming-mfc-atl.md)de bases de datos .

## <a name="see-also"></a>Consulte también

[Uso de vistas](../mfc/using-views.md)
